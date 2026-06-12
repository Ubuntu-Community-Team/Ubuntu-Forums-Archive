---
title: "Help!I can't run wine!"
date: 2006-02-18
forum: General Help
---

### Post by mikeandmore on 2006-02-18
i get it from apt
i get it from the wine.sf.net
i compile it myself!!!
and all of those i have tried!
but all are the same result

```
mike@ubuntu:~$ winecfg
Killed
mike@ubuntu:~$ wineserver -d
sock_init: shutdown() causes EOF
wineserver: starting (pid=5277)
mike@ubuntu:~$ pgrep wineserver
5277
mike@ubuntu:~$ wine
Killed
mike@ubuntu:~$ wine -v
Killed
mike@ubuntu:~$ wine-preloader
Killed
mike@ubuntu:~$ winhelp
Killed
```

after i remove the ~/.wine
i got

```
mike@ubuntu:~$ rm ~/.wine -r
rm: remove write-protected regular file `/home/mike/.wine/wine.inf'? y
mike@ubuntu:~$ winecfg
Killed
mike@ubuntu:~$ wineserver -d
sock_init: shutdown() causes EOF
[COLOR="Red"]Segmentation fault[/COLOR]
mike@ubuntu:~$ wine
Killed
mike@ubuntu:~$ wine-preloader
Killed
```

Help!Anybody has any ideas??

---

### Post by mikeandmore on 2006-02-18
AnyBody??
Please!!!

---

### Post by gremlin hunter on 2006-02-18
Try booting with an older kernel.

---

### Post by DaveRowell on 2006-02-18
You're using Ubuntu 6.10 with Gnome 2.12 desktop - right?  If not ????

Remove /.wine folder from your home directory
Remove any/all old versons of wine that you've installed - uninstall depends on how you installed wine in the first place.  Make sure all wine versions are gone.

System > Administration > Synaptic Package Manager   Search for **wine**   Mark for installation ***wine*** and ***libwine***   Click Apply  This will give you a fresh install of wine 20050725 which should work well for you.

If wine shows as being installed - mark it for complete removal - apply - go back and install only wine and libwine.

Open a terminal window and run winecfg to establish the correct file system within a new .wine folder

Works for you????

There are newer versions of wine, the most current being 0.9.8  If you feel a real need for the newest (I wouldn't suggest it right now) send me a note and I'll show you how to add the wine repository to your sources list

---

### Post by mikeandmore on 2006-02-18
i'm sorry i'm not
i was running on dapper with gnome 2.13.91

maybe my kernel is the problem
cuz in my laste kernel it works great

but now it was just like that
[http://forums.grsecurity.net/viewtopic.php?t=1099&sid=76026bb823629e7529bac790ad5f4f27](http://forums.grsecurity.net/viewtopic.php?t=1099&sid=76026bb823629e7529bac790ad5f4f27)
i just wonder if the ubuntu team turn off the randomization?
thanks 

mike@ubuntu:~$ dpkg -l linux*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
pn  linux-386                     <none>                        (no description available)
ii  linux-686                     2.6.15.14                     Complete Linux kernel on PPro/Celeron/PII/PIII/PIV.
un  linux-doc-2.6.12              <none>                        (no description available)
un  linux-doc-2.6.15              <none>                        (no description available)
un  linux-image                   <none>                        (no description available)
un  linux-image-2.6               <none>                        (no description available)
rc  linux-image-2.6.12-9-386      2.6.12-9.23                   Linux kernel image for version 2.6.12 on 386.
rc  linux-image-2.6.12-9-686      2.6.12-9.23                   Linux kernel image for version 2.6.12 on PPro/Celeron/PII/PIII/PIV.
ii  linux-image-2.6.15-10-686     2.6.15-10.15                  Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP
ii  linux-image-2.6.15-15-686     2.6.15-15.21                  Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP
pn  linux-image-386               <none>                        (no description available)
ii  linux-image-686               2.6.15.14                     Linux kernel image on PPro/Celeron/PII/PIII/PIV.
ii  linux-kernel-headers          2.6.11.2-0ubuntu13            Linux Kernel Headers for development
un  linux-kernel-log-daemon       <none>                        (no description available)
rc  linux-restricted-modules-2.6. 2.6.12.4-11                   Non-free Linux 2.6.12 modules on 386
rc  linux-restricted-modules-2.6. 2.6.12.4-14                   Non-free Linux 2.6.12 NVIDIA legacy module on 386
rc  linux-restricted-modules-2.6. 2.6.12.4-14                   Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII/PIV
rc  linux-restricted-modules-2.6. 2.6.12.4-14                   Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII/PIV
ii  linux-restricted-modules-2.6. 2.6.15.3-4                    Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
ii  linux-restricted-modules-2.6. 2.6.15.5-2                    Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
pn  linux-restricted-modules-386  <none>                        (no description available)
ii  linux-restricted-modules-686  2.6.15.14                     Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.
ii  linux-restricted-modules-comm 2.6.15.5-2                    Non-free Linux 2.6.15 modules helper script
ii  linux-sound-base              1.0.10-4ubuntu3               base package for ALSA and OSS sound systems
un  linux-source-2.6.12           <none>                        (no description available)
un  linux-source-2.6.15           <none>                        (no description available)

---

### Post by mikeandmore on 2006-02-18
by the way
i compile it myself
i thought that's maybe faster and stabler
and actually i compile it with my favorite ICC but that's not the problem
the version i compiled and the apt version got the same output,and the same output if i "strace" them

---

