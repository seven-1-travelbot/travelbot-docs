# Configuration saving

As the main **binary format** of the platform is protobuf. Configuration files are also saved as [protobuf wire](https://protobuf.dev/programming-guides/encoding/) **binaries**.

Every configuration is saved according to its [**protobuf definition**](https://buf.build/seven-1/travelbot) into a **separate** binary file. _Project's_ configuration is saved as a filesystem of these binaries. Project's folder can further be **compressed** to save up space.

Here's an example filesystem:

```filesystem
travelbot/
├── bed74a7bd37c9fd737af2d3e1446c887 (project_2)/
│   ├── project.protbin
│   ├── Map/
│   │   └── 91c776813526d62a377c88a78e113c7f.protobin
│   ├── Missions/
│   │   ├── 2bf8e4a251c1f7e9bc86c16d0e312999.protobin
│   │   └── de0da9cd941d7f68387413196b3dce9a.protobin
│   ├── Dialog Starters/
│   │   ├── 02b3cecb4bc2598a6e05a80e90279a86.protobin
│   │   ├── 3efea4df6407457d621c9beab9290416.protobin
│   │   └── 891a440de7bd48321557bff81b7e20f9.protobin
│   ├── Scrape Configs/
│   │   ├── 7fc4c8415f6848e76ad6bc6f9b779bc8.protobin
│   │   └── e30aaee6672c0f2f66e1dfa58dcd7cb3.protobin
│   ├── UI Configs/
│   │   └── 5e32ad9567a72b3f0fc751573794cc7b.protobin
│   └── Assets/
│       └── logo.png
└── dd76f82f3df49afbb0ec9ad827a88e5a (project_2)/
    └── ...
```

<!-- Use this website https://tree.nathanfriend.io/?s=(%27options!(%27fancy!true~fullPath!false~trailingSlash!true~rootDot!false)~J(%27J%27travelbotFbed74a7bd37c9fd737af2d3e1446c887E*L.HtNMap*B91c776813526d62a377c88a78e113c7f-MissionK2bf8e4a251c1f7e9bc86c16d0e312999Ode0da9cd941d7f68387413196b3dce9a-Dialog%20StarterK02b3cecb4bc2598a6e05a80e90279a86O3efea4df6407457d621c9beab9290416O891a440de7bd48321557bff81b7e20f9-ScrapeG7fc4c8415f6848e76ad6bc6f9b779bc8Oe30aaee6672c0f2f66e1dfa58dcd7cb3-UIG5e32ad9567a72b3f0fc751573794cc7b-AssetKlogo.pngFdd76f82f3df49afbb0ec9ad827a88e5aEF%20...%27)~version!%271%27)*FB-.HtoNB%20%20E%20%7BL_2%7DF%5CnBG%20ConfigKHproJsource!Ks*BLHjectNbin*O-B%01ONLKJHGFEB-* to generate filesystem. -->

So here's a couple of moments to notice:

- travelbot is a **root folder**

- project's folder name is its `project_id`

- `project.protobin` is a special file to contain project's metadata

- project's subfolders are **config types**

- config's file names are their `config_id`s

- `Assets` is a special folder with **media** files to use by UI Configs
