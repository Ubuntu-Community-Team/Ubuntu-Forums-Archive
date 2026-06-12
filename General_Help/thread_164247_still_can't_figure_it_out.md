---
title: "still can't figure it out"
date: 2006-04-22
forum: General Help
---

### Post by sjoseph on 2006-04-22
i am trying to access my Linux files in WinXP, so I created a shared folder using SMB, but i still don't get how to access these files from XP. any ideas. thanks.

---

### Post by Efwis on 2006-04-22
[QUOTE=sjoseph]i am trying to access my Linux files in WinXP, so I created a shared folder using SMB, but i still don't get how to access these files from XP. any ideas. thanks.[/QUOTE]
you have to have a fat32 partition on your Windows hard drive. Then you put your shared folder on that partition and Windows will be able to see it and access it.

---

### Post by Ramses de Norre on 2006-04-22
Are linux and winxp on the same machine? [http://www.fs-driver.org/]("http://www.fs-driver.org/")
Install the driver in windows and you can then assign drive letters to your ext2 and ext3 partitions (throug win's control panel) and browse them through normal explorer.
No need to make additional partitions ;)

---

### Post by sjoseph on 2006-04-22
thanks, i'll try the fs driver.

---

### Post by Ramses de Norre on 2006-04-22
SMB is a network protocol, so it's used to connect computers through a network (just to let you know ;)).

---

### Post by sjoseph on 2006-04-22
thanks, the fs-driver worked great...also thanks for the info about SMB

---

