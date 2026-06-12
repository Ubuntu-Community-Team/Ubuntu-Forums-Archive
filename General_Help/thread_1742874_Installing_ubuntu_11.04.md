---
title: "Installing ubuntu 11.04"
date: 2011-04-29
forum: General Help
---

### Post by comp_007 on 2011-04-29
I posted [here]("http://ubuntuforums.org/showpost.php?p=10736711&postcount=172")but didn't get any response

> @ Friends,

by mistake my partition got deleted where ubuntu 11.04 was residing and due to the same reason i am unable to access it, I also have windows 7 (dual boot),


now i am getting the error
unknown filesystem
grub rescue>

I haven't read this thread since I am posting through mobie, buy is there anny method by which I can log into windows ? I want to install a fresh copy of ubuntu now.

thanks

Now, I found an 8.10 live CD and created a USB startup disk for ubuntu 11.04, the disk was created successfully, but unfortunately when I booted with that disk I got the error

> Unidentified keyword found in configuration file

This error is possibly because of the difference in versions.

Now, it would be great if someone could help me uninstall GRUB using the liveCD or help me install ubuntu 11.04.

Thanks !

---

### Post by comp_007 on 2011-04-29
I found another LiveCD this time ubuntu 10.04 LTS.

But I am still getting the same error

> SYSLINUX 3.63 Debian-2008-07-15 EBIOS Copyright (c) 1994-2008 H. Peter Anvin
Unidentified keyword found in configuration file 
boot:

---

### Post by hhoyt on 2011-04-29
Sorry for your problems.

RE: recovery. Sounds like you would be better off using win recovery:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Once recovered TAKE A FULL BACKUP- a number of good progs, I use Paragon B&R but UI on Macrium reflect may be easier to follow.
Better yet, a full backup as above AND partition backups using FSARCHIVER.


Best of luck, Howard

---

### Post by comp_007 on 2011-04-29
Managed to solve all my problems now.
Found a way to encounter "Unknown Keyword found" error by editing the sysfile.cfg file.

I am posting this through ubuntu 11.04.

Thanks for your help anyways hhyot.

---

### Post by mörgæs on 2011-04-29
Good, please mark the thread 'solved'.

---

