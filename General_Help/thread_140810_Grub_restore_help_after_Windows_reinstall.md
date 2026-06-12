---
title: "Grub restore help after Windows reinstall"
date: 2006-03-07
forum: General Help
---

### Post by Raptor_85 on 2006-03-07
I am having some problems restoring grub.  I recently had to reinstall windows xp, and it disabled grub.  I have been reading some other threads, like this one:   [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

I tried using the install cd, but when it asked to partition, it did not list partitions, just the entire disk under manually edit partitions.  It gave me the option to erase the entire disk.  Thats as far as I got with that option.

I also tried the last part of this page [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29)  
When I do the find /boot/grub/stage1 and it returned hd(0,1) which I thought meant that my grub install was under my root partition.  When i tried to continue with the instructionsand install grub to the HD (not the MBR) it gives me 2 errors the output was:
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/afs_stage1_5" exists... yes
Running "embed /boot/grub/afs_stage1_5 (hd0,1)"... failed (this is not fatal)
Running "embed /boot/grub/aft_stage1_5 (hd0,1)"... failed (this is not fatal)
Running "install /boot/grub/stage1 (hd0,1) /boot/grub/stage2 p /boot/grub/menu.lst "...succeeded
Done. 

Grub was still not restored.

I am not quite sure where to go from here.  I don't know too much about linux, but I think I can install in the MBR with grub-install /dev/hda  but some posts say that this can mess up windows and keep it from loading?  I installed ubuntu with default options and I am not quite sure where grub is to begin with (I know i edit the menu.lst under /boot/grub).  Should I install to the MBR or some other option?

---

### Post by dcstar on 2006-03-07
[QUOTE=Raptor_85]
......
I am not quite sure where to go from here.  I don't know too much about linux, but I think I can install in the MBR with grub-install /dev/hda  but some posts say that this can mess up windows and keep it from loading?  I installed ubuntu with default options and I am not quite sure where grub is to begin with (I know i edit the menu.lst under /boot/grub).  Should I install to the MBR or some other option?[/QUOTE]
Windows replaces the Grub MBR loader, so you do need to replace this to "fix" the Windows loader which has overwritten Grub.

Once you have Grub (and Ubuntu) working, it should be fairly easy to set it up to boot the Windows partition.

---

