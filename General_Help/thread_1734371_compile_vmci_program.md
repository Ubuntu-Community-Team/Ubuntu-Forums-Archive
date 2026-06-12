---
title: "compile vmci program"
date: 2011-04-20
forum: General Help
---

### Post by g-fox on 2011-04-20
hello,

I'm trying to compile the vmware vmci example program and i get errors:

gcc datagramApp.c 
/tmp/ccTmnqXU.o: In function `main':
datagramApp.c.text+0x16c): undefined reference to `VMCI_InitApp'
datagramApp.c.text+0x1be): undefined reference to `VMCI_CleanupApp'
/tmp/ccTmnqXU.o: In function `DoDatagramServer':
datagramApp.c.text+0x1e6): undefined reference to `VMCIDatagram_CreateHnd'
datagramApp.ctext+0x24f): undefined reference to `VMCIDs_Lookup'
datagramApp.c.text+0x2d7): undefined reference to `VMCIResource_AddClientPrivileges'
datagramApp.ctext+0x333): undefined reference to `VMCIDs_Register'
datagramApp.c.text+0x3bf): undefined reference to `VMCIDatagram_RecvFrom'
datagramApp.c.text+0x44f): undefined reference to `VMCIDatagram_SendTo'
datagramApp.c.text+0x4a: undefined reference to `VMCIDs_Unregister'
datagramApp.c.text+0x4c0): undefined reference to `VMCIDatagram_DestroyHnd'
/tmp/ccTmnqXU.o: In function `DoDatagramClient':
datagramApp.c.text+0x505): undefined reference to `VMCIDs_Lookup'
datagramApp.c.text+0x563): undefined reference to `VMCIDatagram_CreateHnd'
datagramApp.c.text+0x60: undefined reference to `VMCIResource_AddClientPrivileges'
datagramApp.c:(.text+0x680): undefined reference to `VMCIDatagram_SendTo'
datagramApp.c:(.text+0x6b: undefined reference to `VMCIDatagram_RecvFrom'
datagramApp.c:(.text+0x6f7): undefined reference to `VMCIDatagram_DestroyHnd'
collect2: ld returned 1 exit status

i have the headers 

tnx for helping

---

### Post by TeoBigusGeekus on 2011-04-20
Compile it with
```
gcc -I/path/to/headers datagramApp.c
```

---

### Post by g-fox on 2011-04-20
I get the same errors.. all the functions are implemented in the vmci kernel module, do i need to add any symbols?

---

