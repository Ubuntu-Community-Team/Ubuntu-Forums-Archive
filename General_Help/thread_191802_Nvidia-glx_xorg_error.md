---
title: "Nvidia-glx xorg error"
date: 2006-06-08
forum: General Help
---

### Post by th3t1nm4n on 2006-06-08
I just installed Dapper x86 after getting tired of trying to get Win32 codecs to work in Dapper x64, and now when I try to enable nvidia-glx I'm getting a problem that I didn't get in x64: ```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

tinman@FragBox:~$ sudo apt-get install nvidia-glx
nvidia-glx             nvidia-glx-legacy      nvidia-glx-src
nvidia-glx-dev         nvidia-glx-legacy-dev
tinman@FragBox:~$ sudo apt-get install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 4059kB of archives.
After unpacking 12.5MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com dapper/restricted nvidia-glx 1.0.8762+2.6.15.11-1 [4059kB]
Fetched 4059kB in 47s (85.9kB/s)
Selecting previously deselected package nvidia-glx.
(Reading database ... 69523 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8762+2.6.15.11-1_i386.deb) ...
Setting up nvidia-glx (1.0.8762+2.6.15.11-1) ...

tinman@FragBox:~$ sudo nvidia-
nvidia-bug-report.sh  nvidia-settings
nvidia-glx-config     nvidia-xconfig
tinman@FragBox:~$ sudo nvidia-
nvidia-bug-report.sh  nvidia-settings
nvidia-glx-config     nvidia-xconfig
tinman@FragBox:~$ sudo nvidia-glx-config
/usr/sbin/nvidia-glx-config called with unknown command:
Usage: /usr/sbin/nvidia-glx-config [enable|disable]
tinman@FragBox:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
tinman@FragBox:~$
```

This was a fresh install, the first thing I did, yet it claims that I've edited my xorg.conf, and if I do ```
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
``` and then try it again it won't complain, but if I kill X and try to start it again I that blue screen that says that your xorg.conf didn't work.

Thanks for any help on this in advance.

<--Edit-->
I just reinstalled Dapper x64 and got the same problem again now, what gives?

---

### Post by Sutekh on 2006-06-08
Just going on the [NVIDIA drivers](http://ubuntuforums.org/showthread.php?t=139264) thread on this forum, you should run
```
sudo nvidia-xconfig
```not nvidia-glx-config.

---

