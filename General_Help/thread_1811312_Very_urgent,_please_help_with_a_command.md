---
title: "Very urgent, please help with a command"
date: 2011-07-24
forum: General Help
---

### Post by BigShoe on 2011-07-24
Hi friends,
I don't know why and how, but from some reason my ubuntu stopped reading the hard drive single partition.
It's very important for me to open the data inside there because all my back up is in there.
When I try to open the partition from the "my computer" explorer, it shows me the error:
"Unable to mount location
Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command."

By the way, I'm have no OS on the hard drive and I use the ubuntu as a live OS from a Flash key.

Thanks a lot for help,
Sincerely yours, Ami.

---

### Post by sanderj on 2011-07-24
Have you tried rebooting?

---

### Post by JC Cheloven on 2011-07-24
The symptoms are that of a bad previous closing of the NTFS filesystem, due for example to a hard "plugout" from the usb, or to a faulty shutdown when the disk was connected to windows. 

AFAIK the easier way to solve that is to connect the disk to windows and let it try to repare the filesystem (as NTFS is a windows fs, it should do a better job at repairing it).

Hope this helps.

---

### Post by BigShoe on 2011-07-25
isn't there any other option just for doing it through linux?

---

### Post by nothingspecial on 2011-07-25
Try ntfsfix

Don't know if it is preinstalled these days so

```
sudo apt-get install ntfsprogs
```

```
sudo ntfsfix /dev/sd??
```

replace the 2 ?s with whatever your ntfs drive is. You can finout by typing ```
sudo fdisk -l
```

---

