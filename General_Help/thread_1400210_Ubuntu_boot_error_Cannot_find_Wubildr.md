---
title: "Ubuntu boot error: Cannot find Wubildr"
date: 2010-02-06
forum: General Help
---

### Post by DukeLono on 2010-02-06
Hi, for several months I've been using an install of Ubuntu on Windows XP on my netbook. Iworked fine until recently, when I tried to boot into Ubuntu I got an error message reading:

Try (hd0,0): FAT32: No WUBILDR
Try (hd0,1): NTFS5: No wubildr
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart.

I've checked for the wubildr file and it's in its usual place on the C: drive, yet I still get this error message. Any solutions? Thanks very much!

---

### Post by camille0704 on 2010-02-07
I have exactly the same problem. I was working on ubuntu when my laptop went out of battery and shut down of it. Then i got this message at reboot:
sh:grub
Possible commands are:
. [ badrun boot cat chainleader configfile cpuid dump echo expert halt help initrd
linux list_env load_env loopback is 1smod parser.rescue parser
.sh reader.normal reader.rescue reboot rmod save_env search set sleep source terminal
_input.console terminal_output. console test unset
 
so i did as advised in this thread: [http://ubuntuforums.org/showthread.php?p=8788468](http://ubuntuforums.org/showthread.php?p=8788468), that is changing the wubildr file according to the one found there: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10),
 
and now, i get just the same message as you did... 
 
If anyone can help us...

---

### Post by JuanOne on 2010-02-11
G'day Mate.

It looks like you lost an important file from C:\.

You need these files to be able to start your Ubuntu.

BOOTSECT.BAK
code.bin
wubuildr
wubildr.mrb

So you either can get those files from someone else who running at same mode or you can download it from [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows). and put into C:\
Let me know if you still having the issue. so I could email those files for u.

JuanOne ;)

---

### Post by vishnu_madhav on 2010-06-27
I too am facing the same problem. Both Ubuntu and Windows were working fine for me for a year, but suddenly today morning I see this problem. In my case, neither is Windows XP starting up, not even with a command prompt. It gives me a blue screen and says something like "A problem has been detected and windows has been shut down to prevent damage to your computer ...". So I am not able to move those files that you mentioned to the C drive, since the dos prompt is not starting up. Any suggestions?

---

