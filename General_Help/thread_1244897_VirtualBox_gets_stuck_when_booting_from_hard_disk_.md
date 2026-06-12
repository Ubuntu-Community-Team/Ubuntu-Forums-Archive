---
title: "VirtualBox gets stuck when booting from hard disk (WinXP)"
date: 2009-08-19
forum: General Help
---

### Post by vze4p6c2 on 2009-08-19
Hello folks!

I have just installed VirtualBox and hoped to be able to access raw disk to book my windows partition.  I have 3.0.4 version of Virtual box and use Ubuntu 9.04.

Basically here what I have done:
1.  Installed VirtualBox from the .deb package that Box provided.
2.  Created a virtual partition that would grant me access to raw drive (sda) using command: 
```
sudo VBoxManage internalcommands createrawvmdk -filename /WinXP.vmdk -rawdisk /dev/sda
```
3. When I start the virtual machine, I am able to see the GRUB and all the partitions.  I am also able to edit various options within grub with no problems.
4.  When I select Windows XP Pro option (and press ENTER to start booting from that partition), it seems that the bar is loading but then stops responding (within about 5 seconds; no Microsoft logo appears) and I am forced to close the window (shutdown virtual machine).

Everything is perfect when I boot from the hard drive naturally into the Windows XP.  Very weird.

Any help would be greatly appreciated.  Any questions will be answered.  Thanks you guys!

---

