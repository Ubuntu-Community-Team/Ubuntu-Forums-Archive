---
title: "accessing nfs shares from windows server 2008?"
date: 2010-02-15
forum: General Help
---

### Post by Face_Man on 2010-02-15
Hello all,

howto accessing nfs shares from windows server 2008?

i install the "Services for Network File System (NFS)" components on windows server 2008 and i was able to mount the share on ubuntu server 9.10 using this command:

```

mount -o timeout=1 \\10.0.1.4\share\ *
Z: is now successfully connected to \\10.0.1.4\share\
the command completed successfully.

```

however, when i try to accessing the mao drive i gwt this error
```

Z:\ is not accessible.
the network path was not found.

```

and i try to access the same NFS share from other linux box and i was able to access it but no luck with windows.

Any help would be much appreciated.

---

### Post by Face_Man on 2010-02-17
anyone!

---

