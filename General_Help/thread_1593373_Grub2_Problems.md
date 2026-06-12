---
title: "Grub2 Problems"
date: 2010-10-11
forum: General Help
---

### Post by hashime on 2010-10-11
I've been having problems with grub the entire length of time I've been using it, minor problems, but irritating ones like not being able to change the default boot entry. I was then offered an upgrade to Grub2, which I thought would solve my problems, which it didn't. Currently I cannot change the default boot entry, I cannot load a splash image, and I cannot delete old boot entries. 
I am not a very experienced user, but have however looked for and attempted many different fixes and tutorials trying to fix the problems. 
I also get this error when updating grub2:
stephen@WINNER:~$ sudo update-grub
[sudo] password for stephen: 
error: cannot open `/dev/sdb' while attempting to get disk size.
error: cannot open `/dev/sdb' while attempting to get disk size.
Generating grub.cfg ...
error: cannot open `/dev/sdb' while attempting to get disk size.
error: cannot open `/dev/sdb' while attempting to get disk size.
error: cannot open `/dev/sdb' while attempting to get disk size.
error: cannot open `/dev/sdb' while attempting to get disk size.
error: cannot open `/dev/sdb' while attempting to get disk size.
error: cannot open `/dev/sdb' while attempting to get disk size.
error: cannot open `/dev/sdb' while attempting to get disk size.
error: cannot open `/dev/sdb' while attempting to get disk size.
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Any help would be appreciated. 
(I tired changing the default entry through the gui and by editing the script file (not grub.cgf) )

---

### Post by oldfred on 2010-10-11
Is your install on sdb? It is saying there is some issue with sdb.

You can set default:

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even grub2.

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)


General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

To remove kernel entries from grub menu you can remove kernels. But you should keep one older one incase the newest has issues.
HOWTO: Remove Older Kernels via GUI
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
Command line:
[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

---

