---
title: "File System Problems After Install"
date: 2012-01-14
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2012-01-14
I have a new Dell XPS-17 laptop on which I just installed Xubuntu 11.10. I wanted to delete Windows completely and use the entire hard drive (1 TB) for Linux, but the hard drive the machine came with was partitioned (I guess?) into two discs, and the ubuntu installer would only let me choose one or the other, so I chose one partition, thinking I could expand it later. I also chose to use an encrypted LVM.  Windows seems to have been partially retained; it boots first when the computer starts, but never progresses beyond the Windows logo. The screen just stays blank after that. When I access the boot menu, Windows isn't even there, and I can't access ubuntu directly, I have to use the recovery console. After that, everything works fine.   I opened up gparted and it seems there is an error with the encryption. Under /dev/sda2, there is a sub-entry, /dev/sda5, with file system crypt-luks, and a red exclamation mark next to it. When I click on Information in the context menu, it's status is "not mounted", and there is the warning &quot;Linux Unified Key Setup encryption is not yet supported.&quot;   How do I fix this error and allocate all the disc space to my linux installation? I thought maybe I just needed to mount crypt-luks, but I don't understand the manual mounting instructions here:  [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)  specifically, the step &quot;For every location ('/media/windows'), run the following command.'' I thought there was only one /media/windows on the whole linux filesystem...?

---

### Post by Tk007LwZFJW5ej on 2012-01-14
So far, I've found out that encrypted partitions show up weird in gparted, and that doesn't reflect a problem with the partition.      Somehow, grub was not available; I downloaded it, but it has not made much of a difference. I was able to boot into ubuntu *once* without going through the recovery option first, and the session ended up hanging on the title screen, where it indicated it was mounting the partition.   
   I've tried boot repair, but it always ends up asking me if I want to assemble a RAID array, then quits regardless of my answer. 
   I don't understand why Windows is booting first. I tried changing the boot order of the hard drives(I guess it wasn't a single drive that was partitioned after all, since they were listed as separate drives in the setup list) in system setup, and Windows still boots first.
   Mainly, I need to be able to get linux to boot first.

---

