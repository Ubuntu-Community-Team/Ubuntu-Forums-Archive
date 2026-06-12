---
title: "akonadiserver problem.."
date: 2009-10-31
forum: General Help
---

### Post by mathfeel on 2009-10-31
It does not start successfully:
```
$ akonadiserver 
Database "akonadi" opened using driver "QMYSQL" 
DbInitializer::run() 
checking table  "SchemaVersionTable" 
checking table  "ResourceTable" 
checking table  "CollectionTable" 
checking table  "MimeTypeTable" 
checking table  "PimItemTable" 
checking table  "FlagTable" 
checking table  "PartTable" 
checking table  "CollectionAttributeTable" 
checking relation  "PimItemFlagRelation" 
checking relation  "CollectionMimeTypeRelation" 
checking relation  "CollectionPimItemRelation" 
DbInitializer::run() done 
skipping update 2 
skipping update 3 
skipping update 4 
skipping update 8 
skipping update 10 
skipping update 12 
Nepomuk QueryServer interface not available! 
Unable to connect to dbus service:  ""
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8051f25]
1: akonadiserver [0x80523f6]
2: [0xdda400]
3: [0xdda422]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x80c4d1]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x80f932]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0x1e7f8c]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8052f54]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x85) [0x27a0d5]
9: /usr/lib/libQtCore.so.4 [0x288ed5]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0x28a298]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x804dbf3]
12: akonadiserver(main+0x499) [0x804d169]
13: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x7f8b56]
14: akonadiserver [0x804cc01]
]
"

```

Help?

---

