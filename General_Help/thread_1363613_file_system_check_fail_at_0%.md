---
title: "file system check fail at 0%"
date: 2009-12-24
forum: General Help
---

### Post by joshuntu on 2009-12-24
Hello, i am using ubuntu 9.1 and i have been using it since the day it came out without any problems. today i tried to turn on the computer and on the ubuntu loading screen it started to do a file system check which started at 0% and the option to press esc to cancel check was also given (which by the way does nothing) and when my file system check beggins it stays at zero percent for a while and then brings me to a maintanence shell page that says that loading of the file system failed or it could not find the file system or something like that and gives me the option to press controle d to retry, if i press controle d it tries again and brings me right back to the same mantenence shell page. pressing escape or restarting the computer changes nothing. any suggestions_??? thanks for the help.

josh

---

### Post by ticthak@AOL.com on 2009-12-24
try your LiveCD or another good Linux boot disk like UBCD,Knoppix, Rescue, etc. and you can have access to a lot of repair tools like gparted (to check your partitioning and filesystems), fsck (ditto), lots of others; "gpart" (not gparted) just saved my butt last month when all of my NTFS partitions vanished (that, by the way, is not your problem). Chances are you'll need the Koala CD though, as you're install is probably ext4 and earlier versions of the tools are included on these other disks- the Koala CD doesn't have all the tools available with other disks

---

### Post by fragos on 2009-12-24
I suggest you boot from the Live CD you used to install Ubuntu. It doesn't need the hard disk to run but at least you'll be able to take a look at the system and diagnose your problem.  You can open a terminal session with no disks mounted so you can perform testing. "fsck" may be helpful. Also helpful may be "testdisk" which you'd need to install to use.

---

