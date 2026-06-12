---
title: "Free space vs Available space confusions"
date: 2009-10-13
forum: General Help
---

### Post by GwilymHardy on 2009-10-13
I've looked around the forum for threads regarding the free space/ available space on a disk, but I can't find anything that explains my confusion.

I have an Eee PC 901 with Ubuntu 8.10. The Ubuntu installation is on a 4GB SSD, with the Home folder on a 16GB SSD. I noticed today that whilst I had (on the 4GB SSD) 250+MB marked as 'free', I had 0 bytes markedd as 'available'. I understand that Ubuntu is meant to allocate 5% of the disk space for safe boots, but normally I have perhaps 300MB 'free' and 250+ 'available'. This is a sudden change.

I deleted some programs, so I managed to get 300MB as 'free' and 110MB (ish) as 'available'. I then installed a 100MBish program (secret maryo), uninstalled it, and found I only had 80MB marked as 'available', rather than the 110ish I'd had before that installation.

Any ideas what caused this? This huge difference between free and available must have appeared in the last month and a half - I pay attention to the space I have on this 4GB because (after ubuntu is installed) I only have 300ish MB left.

If anyone has an explanation I'd appreciate help

Thanks.

Ps - Sorry if this has come up before, but I did do several searches on the forum before typing.

---

### Post by XCan on 2009-10-13
I've no experience from SSD disks, but I wonder how you checked the disk space, was it using ```
 df 
``` ? On my machines, I only have the columns Filesystem, Size, Used, Avail, Use%, Mounted on. Maybe it's different in SSD disks?

If it is, perhaps it could have something to do with the famous "limitation (at least before Intel figured out how to alleviate it)" that such disks are only able to delete a whole block but not a single cell? However, if this is the case, you should be able to write to the disk even though it seems full, it will just have a huge amplification factor (wear) when you do. On the other hand, if your controller chip is amongst the old generation, you already have a huge amplification factor.

---

### Post by GwilymHardy on 2009-11-05
I'm not sure I understand your advice, sorry. I've just uninstalled Open Office, to install version 3.1.1. After the installation I had save error messages, and after logging off and logging back on the session wouldn't begin - not enough space. So I restarted the computer and started a session. Uninstalled Open Office. I now have 426mb FREE and 245mb AVAILABLE. So I have relatively less available than before. Can't install open office, so am worried I'm losing disk space.

---

### Post by dcstar on 2009-11-05
> **GwilymHardy said:**
> 
.........
I deleted some programs, so I managed to get 300MB as 'free' and 110MB (ish) as 'available'. I then installed a 100MBish program (secret maryo), uninstalled it, and found I only had 80MB marked as 'available', rather than the 110ish I'd had before that installation.
.........

Uninstalling does not necessarily remove all the files. Look in /var/log for large files - if you have errors in your logs then they can fill a disk very quickly.

There are many posts already on cleaning out your root filesystem.

---

### Post by alphaniner on 2009-11-05
If you install something through Synaptic/aptitude/apt-get and then uninstall it, the archive(s) (.deb files) from which the program was installed may not get removed.  These archives are located in /var/cache/apt/archives.  You can remove them manually or check the man page of apt-get for the 'clean' options.

---

