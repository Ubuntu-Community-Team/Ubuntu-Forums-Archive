---
title: "Can't uncompress a file in a Network attached storage"
date: 2011-07-05
forum: General Help
---

### Post by Parapan on 2011-07-05
Hello all,

I have a fairly simple setup for my Network attached storage. 

I have a 1TB external hard drive connected to my Asus RT-N16 router through USB. I have enabled file sharing in the router, and thus the hard drive shows up on the network as a shared folder. No hassles, I can read and write to it.

Because I want to use this hard drive for networked backups, I tried to get it to mount on boot with fstab. Here is the line in my fstab file : 

```
//192.168.1.1/SharedFolder   /media/SharedFolder   smbfs   guest,_netdev   0 0
```It mounts fine, no problems, and once again I'm able to read and write files to it. The problem occurs when I try to access the mounted drive and uncompress an archive file for the duplicity backup program. It gives me a list of messages showing that all the files inside the archive failed to uncompress because of error messages like these : 

```
...
tar: duplicity-0.6.13/rdiffdir.1: Cannot utime: Operation not permitted
tar: duplicity-0.6.13/po/io/duplicity.mo: Cannot utime: Operation not permitted
tar: duplicity-0.6.13/po/io/io.po: Cannot utime: Operation not permitted
tar: duplicity-0.6.13/po/io: Cannot utime: Operation not permitted
tar: duplicity-0.6.13/po/io: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: duplicity-0.6.13/po/en_GB/en_GB.po: Cannot utime: Operation not permitted
...
```If I try to extract the same archive by manually going to Network >  RT-N16 (Router) > Shared Folder, it extracts fine. But I need this folder to be mounted on boot because I use it very frequently.

I tried changing smbfs to cifs and it still didn't work. Please not that my knowledge of samba, network storage and file systems is very basic. I tried searching the internet for more information about this but wasn't able to find much information that pertains to this particular problem. Hoping the linux pros here could give me some pointers :D

Thanks in advance!

---

### Post by dcstar on 2011-07-05
> **Parapan said:**
> Hello all,

I have a fairly simple setup for my Network attached storage. 

I have a 1TB external hard drive connected to my Asus RT-N16 router through USB. I have enabled file sharing in the router, and thus the hard drive shows up on the network as a shared folder. No hassles, I can read and write to it.

Because I want to use this hard drive for networked backups, I tried to get it to mount on boot with fstab. Here is the line in my fstab file : 

```
//192.168.1.1/SharedFolder   /media/SharedFolder   smbfs   guest,_netdev   0 0
```It mounts fine, no problems, and once again I'm able to read and write files to it. The problem occurs when I try to access the mounted drive and uncompress an archive file for the duplicity backup program. It gives me a list of messages showing that all the files inside the archive failed to uncompress because of error messages like these : 

```
...
tar: duplicity-0.6.13/rdiffdir.1: Cannot utime: Operation not permitted
tar: duplicity-0.6.13/po/io/duplicity.mo: Cannot utime: Operation not permitted
tar: duplicity-0.6.13/po/io/io.po: Cannot utime: Operation not permitted
tar: duplicity-0.6.13/po/io: Cannot utime: Operation not permitted
tar: duplicity-0.6.13/po/io: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: duplicity-0.6.13/po/en_GB/en_GB.po: Cannot utime: Operation not permitted
...
```If I try to extract the same archive by manually going to **Network >  RT-N16 (Router) > Shared Folder**, it extracts fine. But I need this folder to be mounted on boot because I use it very frequently.
.........

When you mount the drive the **second way** run the following command and look at the actual mount options Ubuntu used, and duplicate them in the fstab file:
```

sudo mount
```

---

### Post by Parapan on 2011-07-05
I tried looking for the line in fstab, but it seems like it doesn't actually mount it even though I can browse the folder through the network. I guess I'll try some other alternative like SSH or FTP mounting for now, thanks anyways!

---

