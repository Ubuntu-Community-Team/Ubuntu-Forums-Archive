---
title: "Can't start firefox after manual power off / Could not find compatible GRE..."
date: 2009-11-01
forum: General Help
---

### Post by rminkler on 2009-11-01
I'm running the 2.6.32 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and using the xorg crack pushers ppa, and the combination of the two caused my system to fail to suspend. 

Because of the failed suspend I had to manually power down the system, and then I had to run fsck and fix about 100 issues to get the system to boot.

When I got to the desktop and tried to start firefox I noticed that the firefox icon was missing from the applications>internet menu, and clicking the text did nothing. 

trying to start firefox from the command line did nothing - no errors, no firefox, just a new prompt.

running dpkg --configure -a brought up errors with two packages, which I fixed by reinstalling them (libaiksaurus and libgnomecups). 

Now when I try to start firefox from the command line I get the following error:

```
Could not find compatible GRE between version 1.9.1 and 1.9.1.*.

```

Some googleing suggested that I should run "xulrunner -register-global," which brings up the following error.

```
rminkler@Crassostrea-Gigas:~$ xulrunner -register-global
*** buffer overflow detected ***: /usr/lib/xulrunner/xulrunner-bin terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f0af472b5f7]
/lib/libc.so.6[0x7f0af472a5a0]
/lib/libc.so.6[0x7f0af472abfb]
/usr/lib/libxul.so.0d(XRE_GetFileFromPath+0x43)[0x7f0af54f85d3]
/usr/lib/xulrunner/xulrunner-bin[0x4017f5]
/usr/lib/xulrunner/xulrunner-bin[0x402125]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f0af4652abd]
/usr/lib/xulrunner/xulrunner-bin[0x4015c9]
======= Memory map: ========
00400000-00404000 r-xp 00000000 08:01 1452137                            /usr/lib/xulrunner/xulrunner-bin
00603000-00604000 r--p 00003000 08:01 1452137                            /usr/lib/xulrunner/xulrunner-bin
00604000-00605000 rw-p 00004000 08:01 1452137                            /usr/lib/xulrunner/xulrunner-bin
01ea8000-01ec9000 rw-p 00000000 00:00 0                                  [heap]
7f0aecdfb000-7f0aecdfe000 r-xp 00000000 08:01 69                         /lib/libuuid.so.1.3.0
7f0aecdfe000-7f0aecffe000 ---p 00003000 08:01 69                         /lib/libuuid.so.1.3.0
7f0aecffe000-7f0aecfff000 r--p 00003000 08:01 69                         /lib/libuuid.so.1.3.0
7f0aecfff000-7f0aed000000 rw-p 00004000 08:01 69                         /lib/libuuid.so.1.3.0
7f0aed000000-7f0aed017000 r-xp 00000000 08:01 264975                     /usr/lib/libICE.so.6.3.0
7f0aed017000-7f0aed216000 ---p 00017000 08:01 264975                     /usr/lib/libICE.so.6.3.0
7f0aed216000-7f0aed217000 r--p 00016000 08:01 264975                     /usr/lib/libICE.so.6.3.0
7f0aed217000-7f0aed218000 rw-p 00017000 08:01 264975                     /usr/lib/libICE.so.6.3.0
7f0aed218000-7f0aed21b000 rw-p 00000000 00:00 0 
7f0aed21b000-7f0aed237000 r-xp 00000000 08:01 893                        /lib/libselinux.so.1
7f0aed237000-7f0aed436000 ---p 0001c000 08:01 893                        /lib/libselinux.so.1
7f0aed436000-7f0aed437000 r--p 0001b000 08:01 893                        /lib/libselinux.so.1
7f0aed437000-7f0aed438000 rw-p 0001c000 08:01 893                        /lib/libselinux.so.1
7f0aed438000-7f0aed439000 rw-p 00000000 00:00 0 
7f0aed439000-7f0aed44f000 r-xp 00000000 08:01 135                        /lib/libresolv-2.10.1.so
7f0aed44f000-7f0aed64e000 ---p 00016000 08:01 135                        /lib/libresolv-2.10.1.so
7f0aed64e000-7f0aed64f000 r--p 00015000 08:01 135                        /lib/libresolv-2.10.1.so
7f0aed64f000-7f0aed650000 rw-p 00016000 08:01 135                        /lib/libresolv-2.10.1.so
7f0aed650000-7f0aed652000 rw-p 00000000 00:00 0 
7f0aed652000-7f0aed657000 r-xp 00000000 08:01 265025                     /usr/lib/libXdmcp.so.6.0.0
7f0aed657000-7f0aed856000 ---p 00005000 08:01 265025                     /usr/lib/libXdmcp.so.6.0.0
7f0aed856000-7f0aed857000 rw-p 00004000 08:01 265025                     /usr/lib/libXdmcp.so.6.0.0
7f0aed857000-7f0aed859000 r-xp 00000000 08:01 265014                     /usr/lib/libXau.so.6.0.0
7f0aed859000-7f0aeda58000 ---p 00002000 08:01 265014                     /usr/lib/libXau.so.6.0.0
7f0aeda58000-7f0aeda59000 r--p 00001000 08:01 265014                     /usr/lib/libXau.so.6.0.0
7f0aeda59000-7f0aeda5a000 rw-p 00002000 08:01 265014                     /usr/lib/libXau.so.6.0.0
7f0aeda5a000-7f0aeda61000 r-xp 00000000 08:01 137                        /lib/librt-2.10.1.so
7f0aeda61000-7f0aedc60000 ---p 00007000 08:01 137                        /lib/librt-2.10.1.so
7f0aedc60000-7f0aedc61000 r--p 00006000 08:01 137                        /lib/librt-2.10.1.so
7f0aedc61000-7f0aedc62000 rw-p 00007000 08:01 137                        /lib/librt-2.10.1.so
7f0aedc62000-7f0aedc6a000 r-xp 00000000 08:01 265006                     /usr/lib/libSM.so.6.0.0
7f0aedc6a000-7f0aede69000 ---p 00008000 08:01 265006                     /usr/lib/libSM.so.6.0.0
7f0aede69000-7f0aede6a000 r--p 00007000 08:01 265006                     /usr/lib/libSM.so.6.0.0
7f0aede6a000-7f0aede6b000 rw-p 00008000 08:01 265006                     /usr/lib/libSM.so.6.0.0
7f0aede6b000-7f0aede98000 r-xp 00000000 08:01 430                        /lib/libpcre.so.3.12.1
7f0aede98000-7f0aee097000 ---p 0002d000 08:01 430                        /lib/libpcre.so.3.12.1
7f0aee097000-7f0aee098000 r--p 0002c000 08:01 430                        /lib/libpcre.so.3.12.1
7f0aee098000-7f0aee099000 rw-p 0002d000 08:01 430                        /lib/libpcre.so.3.12.1
7f0aee099000-7f0aee0bf000 r-xp 00000000 08:01 443                        /lib/libexpat.so.1.5.2
7f0aee0bf000-7f0aee2bf000 ---p 00026000 08:01 443                        /lib/libexpat.so.1.5.2
7f0aee2bf000-7f0aee2c1000 r--p 00026000 08:01 443                        /lib/libexpat.so.1.5.2
7f0aee2c1000-7f0aee2c2000 rw-p 00028000 08:01 443                        /lib/libexpat.so.1.5.2
7f0aee2c2000-7f0aee2c9000 r-xp 00000000 08:01 266055                     /usr/lib/libxcb-render.so.0.0.0
7f0aee2c9000-7f0aee4c9000 ---p 00007000 08:01 266055                     /usr/lib/libxcb-render.so.0.0.0
7f0aee4c9000-7f0aee4ca000 r--p 00007000 08:01 266055                     /usr/lib/libxcb-render.so.0.0.0
7f0aee4ca000-7f0aee4cb000 rw-p 00008000 08:01 266055                     /usr/lib/libxcb-render.so.0.0.0
7f0aee4cb000-7f0aee4ce000 r-xp 00000000 08:01 266053                     /usr/lib/libxcb-render-util.so.0.0.0
7f0aee4ce000-7f0aee6cd000 ---p 00003000 08:01 266053                     /usr/lib/libxcb-render-util.so.0.0.0
7f0aee6cd000-7f0aee6ce000 r--p 00002000 08:01 266053                     /usr/lib/libxcb-render-util.so.0.0.0
7f0aee6ce000-7f0aee6cf000 rw-p 00003000 08:01 266053                     /usr/lib/libxcb-render-util.so.0.0.0
7f0aee6cf000-7f0aee6e8000 r-xp 00000000 08:01 265239                     /usr/lib/libdirect-1.2.so.0.7.0
7f0aee6e8000-7f0aee8e7000 ---p 00019000 08:01 265239                     /usr/lib/libdirect-1.2.so.0.7.0
7f0aee8e7000-7f0aee8e8000 r--p 00018000 08:01 265239                     /usr/lib/libdirect-1.2.so.0.7.0
7f0aee8e8000-7f0aee8e9000 rw-p 00019000 08:01 265239                     /usr/lib/libdirect-1.2.so.0.7.0
7f0aee8e9000-7f0aee8ea000 rw-p 00000000 00:00 0 
7f0aee8ea000-7f0aee8f3000 r-xp 00000000 08:01 265326                     /usr/lib/libfusion-1.2.so.0.7.0
7f0aee8f3000-7f0aeeaf2000 ---p 00009000 08:01 265326                     /usr/lib/libfusion-1.2.so.0.7.0
7f0aeeaf2000-7f0aeeaf3000 r--p 00008000 08:01 265326                     /usr/lib/libfusion-1.2.so.0.7.0Aborted

```

Any ideas?

---

### Post by lovinglinux on 2009-11-01
Go to Synpatic and mark **firefox** and **firefox-3.x** (according to your version) for re-installation and apply.

A new profile would also be advised, after such corruption events.

Start Firefox with this:

```
firefox -P
```

Create a new profile with the Profile manager and start it.

---

### Post by rminkler on 2009-11-01
Thanks for the suggestion.

I reinstalled firefox and firefox-3.5 using synaptic, but I'm still getting the error.

```
rminkler@Crassostrea-Gigas:~$ firefox -P
Could not find compatible GRE between version 1.9.1 and 1.9.1.*.
rminkler@Crassostrea-Gigas:~$ 

```

---

### Post by lovinglinux on 2009-11-01
> **rminkler said:**
> Thanks for the suggestion.

I reinstalled firefox and firefox-3.5 using synaptic, but I'm still getting the error.

```
rminkler@Crassostrea-Gigas:~$ firefox -P
Could not find compatible GRE between version 1.9.1 and 1.9.1.*.
rminkler@Crassostrea-Gigas:~$ 

```

Go to Synaptic and re-install **xulrunner-1.9.1**

---

### Post by rminkler on 2009-11-01
Re-installed xulrunner and xulrunner-1.9.1, but I'm still getting the same result.

---

### Post by rminkler on 2009-11-01
Scratch that, now firefox starts but I'm getting a small window with this:

```
XML Parsing Error: undefined entity
Location: chrome://mozapps/content/profile/profileSelection.xul
Line Number 53, Column 1:<dialog

```

I renamed /usr/lib64/xulrunner/chrome/toolkit/content/mozapps/profile/profileSelection.xul in hopes that a new one would be generated, but that doesn't seem to have solved the problem. This is with the "firefox -P" command.

---

### Post by lovinglinux on 2009-11-01
I don't know what else to do. [Try these](http://www.google.com/search?q=Could+not+find+compatible+GRE+between+version+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

---

### Post by rminkler on 2009-11-01
Firefox is working again after marking it for complete removal in synaptic and then installing it again.

Thanks for your help!

---

### Post by lovinglinux on 2009-11-01
> **rminkler said:**
> Firefox is working again after marking it for complete removal in synaptic and then installing it again.

Thanks for your help!

You are welcome. Glad you fixed it.

---

