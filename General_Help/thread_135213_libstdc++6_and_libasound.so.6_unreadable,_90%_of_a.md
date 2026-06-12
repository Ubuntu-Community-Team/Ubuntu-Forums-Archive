---
title: "libstdc++6 and libasound.so.6 unreadable, 90% of applications won't run"
date: 2006-02-23
forum: General Help
---

### Post by CookedGryphon on 2006-02-23
I was uninstalling kaffine and there was a problem with synaptic, soon afterwards, new apps wouldn't start up, and it started coming up with the error messages like the following:
> <~>: gnome-panel
gnome-panel: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
<~>: apt-get
apt-get: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
Notice the lack of gnome and apt-get :-? !!!
XFCE still works and i can boot failsafe and also firefox runs quite happily, just very little else. I tried downloading the libstdc++6, libasound and libc6 packages manually and installing them with dpkg (which still works) but got the output:
> <~/My Downloads>: sudo dpkg -i libasound2_1.0.9-2_i386.deb libc6_2.3.5-1ubuntu12
_i386.deb libstdc++6_4.0.1-4ubuntu9_i386.deb 
Password:
(Reading database ... 142639 files and directories currently installed.)
Preparing to replace libasound2 1.0.9-2 (using libasound2_1.0.9-2_i386.deb) ...
Unpacking replacement libasound2 ...
dpkg: error processing libasound2_1.0.9-2_i386.deb (--install):
 unable to make backup link of `./usr/bin/aserver' before installing new version
: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libc6 2.3.5-1ubuntu12 (using libc6_2.3.5-1ubuntu12_i386.deb
) ...
Unpacking replacement libc6 ...
Preparing to replace libstdc++6 4.0.1-4ubuntu9 (using libstdc++6_4.0.1-4ubuntu9_
i386.deb) ...
Unpacking replacement libstdc++6 ...
dpkg: error processing libstdc++6_4.0.1-4ubuntu9_i386.deb (--install):
 unable to make backup link of `./usr/lib/libstdc++.so.6.0.5' before installing 
new version: Operation not permitted
Setting up libc6 (2.3.5-1ubuntu12) ...
Current default timezone: 'Europe/London'.
Local time is now:      Thu Feb 23 17:55:42 GMT 2006.
Universal Time is now:  Thu Feb 23 17:55:42 UTC 2006.
Run 'tzconfig' if you wish to change it.

Errors were encountered while processing:
 libasound2_1.0.9-2_i386.deb
 libstdc++6_4.0.1-4ubuntu9_i386.deb
OK, so I figure libstdc++6 unreadable, let's check the permissions, so i go to /usr/lib and do:
> </usr/lib>: ls -la | grep libst || libasou
lrwxrwxrwx      1 root       root                34 2005-10-13 15:08 libstartup-notification-1.so.0 -> libstartup-notification-1.so.0.0.0
-rw-r--r--      1 root       root             30832 2005-04-15 11:16 libstartup-notification-1.so.0.0.0
lrwxrwxrwx      1 root       root                18 2006-02-23 15:36 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r--      1 root       root            737496 2005-09-16 10:24 libstdc++.so.5.0.7
br-x--S-wx    117 1698919538 1953628275 613, 476995 1970-01-01 01:00 libstdc++.so.6
?--xrw--wx     32    7929957    6881377     6488096 1970-03-25 11:31 libstdc++.so.6.0.5
-rw-r--r--      1 root       root            793436 2005-07-26 12:52 libstlport_gcc.so.4.6
Notice the weird permissions, and as for the owner! So I did a search for weird file permissions and got:
> </usr/lib>: ls -la | grep ?-
?---r-----     32    7733365    6357037     6881395 1970-03-04 23:59 libasound.so.2
?--xr--rwx  30049    7143534    2125397     7602273 1970-01-01 01:00 libasound.so.2.0.0
?---r-xr-x    114 1852768288 1702035567     7274595 1970-03-18 15:40 libfribidi.so.0.0.0
?--xrw--wx     32    7929957    6881377     6488096 1970-03-25 11:31 libstdc++.so.6.0.5
</usr/lib>: ls -la | grep S-
br-x--S-wx    117 1698919538 1953628275 613, 476995 1970-01-01 01:00 libstdc++.so.6


Please could somebody tell me how to get my system back because I really don't want to have to do a reinstall, everything is just the way I want it, this has been my only computer for about a year now and i've customised just about every aspect and the thought of having to go through and re-install all the packages scares me! Thanks for reading. :)

---

### Post by CookedGryphon on 2006-02-23
Please help me, I **need** this computer to do my work.

---

### Post by CookedGryphon on 2006-02-23
Looking through /usr/lib there are more files with weird permissions:
> ?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libwnck-1.so.18
?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libwnck-1.so.18.0.3
br-x--S-wx    117 1698919538 1953628275    101, 67 Jan  1  1970 libstdc++.so.6
?--xrw--wx     32    7929957    6881377    6488096 Mar 25  1970 libstdc++.so.6.0.5
?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libnautilus-burn.so.2
?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libnautilus-burn.so.2.0.1
?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libXRes.so.1
?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libXRes.so.1.0.0
?---r-----     32    7733365    6357037    6881395 Mar  4  1970 libasound.so.2
?--xr--rwx  30049    7143534    2125397    7602273 Jan  1  1970 libasound.so.2.0.0
?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libcompface.so.1
?---r-xr-x    114 1852768288 1702035567    7274595 Mar 18  1970 libfribidi.so.0.0.0
?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libgksu1.2.so.0
?rwsrwsrwt  65535 4294967295 4294967295 4294967295 Dec 31  1969 libgksu1.2.so.0.0.2


Can anyone spot any patterns here? Does this indicate a corrupted filesystem? Am I going to have to do a fuill reinstall? If so is there any way to save my package list and download all the same ones again? If i save my home partition, will all my apps have the same settings, or will they try and overwrite them when installing? Is there any way to salvage these files? I can't delete and replace them with working versions because they aren't readable by anybody and aren't owned by root even!

---

### Post by CookedGryphon on 2006-02-23
If I only had a way of removing these files so i could reinstall them!, but as they aren't owned by anybody and it won't let me create a user with that name, then there's nothign i can do! Anything i try it says permission denied.

---

### Post by CookedGryphon on 2006-02-24
:( Does nobody have any idea what I can  do?

---

### Post by jasonli on 2006-02-24
Hey Gryphon

I don't know what's really wrong with your computer. But last time when my filesystem got something wrong, I booted up with a livecd and in the terminal, you can try:

fsck

this will probably force check your filesystem and fix errors. Hope you will find this useful.

Good luck!

---

### Post by CookedGryphon on 2006-02-24
nope, no luck, i'm gna download the breezy disk image i think and reinstall my system partition, hopefully this won't override all my settings and all i'll have to do is reinstall packages (tho this in itself is gna be a big job)

---

