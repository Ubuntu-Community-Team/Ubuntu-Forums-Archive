---
title: "fglrx package problem, locked in remove state"
date: 2006-06-02
forum: General Help
---

### Post by acketon on 2006-06-02
I have a package problem that has cropped up and I can't get it to go away.
Somewhere along the lines of trying to get proper 3d support working with the lastest ATI driver 8.25 I have run into a problem. 

I get the following error anytime I try and install/remove packages in apt-get:
E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2

It seems the package xorg-driver-fglrx is marked to be removed, but won't uninstall, I cannot seem to unmark it. I've tried reinstalling, removing all the fglrx  packages and I can't stop this problem. Now I cannot install any other packages or updates because of this error.

here is what i get when trying to remove the package at the command line:
```
acketon@ubuntu:~$ sudo apt-get remove xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 65 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 26.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 182960 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
acketon@ubuntu:~$

```


I've been running dapper since about flight 3/4.

---

### Post by pRedat0r on 2006-06-02
I had this problem a few weeks ago, all I did was 

sudo mv /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.old

then I ran the removal again and it worked fine.  After I did that I just deleted the old file.  Not sure if that was the best way, but right after I did this I installed a newer fglrx driver and everything is working just fine.

hope that helps.  If you are paranoid about breaking something you can just leave the .old file around, I figured i could just reinstall the old driver again if i wanted to revert back.

---

### Post by Galban on 2006-06-02
Hi...

PrEdat0r is right that is the solution. I did it a little bit differnt but, to do same thing. I got resolved this problem thanks to the help of this wonderfull Ubuntu Frorums people. Here is the the how to fix it that was in that thread opened when Dapper was on devel.

[http://www.ubuntuforums.org/showthread.php?t=184627](http://www.ubuntuforums.org/showthread.php?t=184627)

---

