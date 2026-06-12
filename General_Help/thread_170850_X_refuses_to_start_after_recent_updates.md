---
title: "X refuses to start after recent updates"
date: 2006-05-05
forum: General Help
---

### Post by simohell on 2006-05-05
After some 60-70 updated packages my until then working X.org fails to start.

This appears to be hardware related, since the same updates did work on my other laptop. Also X works if using vesa-driver insted of mga. Mga-driver however worked perfectly until some of the updates messed things up.

Is there any way to undo updates?

(I can't work using the non-native resolution on TFT, since vesa doesn't go that high.
Maybe it is time to try and update to Dapper...)

---

### Post by rcarring on 2006-05-05
Hi

Please see

[http://www.ubuntuforums.org/showthread.php?t=170795](http://www.ubuntuforums.org/showthread.php?t=170795)

This should help.

R

NB If you are running Breezy Badger on a "real" machine, the steps I took may not work for you, but I think they might.

---

### Post by simohell on 2006-05-05
No, it doen't do anything -- I just get "... is alredy the newest version".

It is not, that X isn't there. The problem is that it doent work.

---

### Post by simohell on 2006-05-05
This is the gdm log:
```
X Window System Version 6.8.2 (Ubuntu 6.8.2-77.1 20060503192905 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.12 i686 [ELF] 
Current Operating System: Linux Tar-Minyatur 2.6.12-10-386 #1 Fri Apr 28 13:13:44 UTC 2006 i686
Build Date: 03 May 2006
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Fri Apr 28 13:13:44 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May  5 19:07:18 2006
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Required symbol MGAValidateMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol XAAGetScreenIndex from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol XAAGetCachePlanarMonoStipple from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol XAAGetCachePlanarMonoStipple from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol XAAGetScreenIndex from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol XAAGetScreenIndex from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol XAAGetCachePlanarMonoStipple from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAGetHardwareInfo from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAOpenLibrary from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAGetBOARDHANDLESize from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAGetHardwareInfo from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAOpenLibrary from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAGetBOARDHANDLESize from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAValidateVideoParameters from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAValidateMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGACloseLibrary from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol HALSetDisplayStart from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol HALSetDisplayStart from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAGetHardwareInfo from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAOpenLibrary from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAGetBOARDHANDLESize from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGAValidateMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGACloseLibrary from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGACloseLibrary from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGARestoreVgaState from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASetVgaMode from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Required symbol MGASaveVgaState from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86Int10AllocPages from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86Int10FreePages from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExtendedInitInt10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86Int10FreePages from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86int10Addr from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86Int10AllocPages from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!
Symbol xf86ExecX86int10 from module /usr/X11R6/lib/modules/libvbe.a is unresolved!

Fatal server error:
Some required symbols were unresolved


Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

---

### Post by simohell on 2006-05-05
Replacing the mga drivers solved it.

---

### Post by timw on 2006-05-08
I'm having exactly the same problem.

What did you replace the mga driver with?

---

### Post by peaceful_dragon on 2006-05-08
[QUOTE=simohell]Replacing the mga drivers solved it.[/QUOTE]

I too am having the exact same problem. I downloaded a new driver from Matrox and when I tried to install it it said something like "files are the same, not installing".

How exactly did you replace the drivers?

---

### Post by peaceful_dragon on 2006-05-08
OK, so I deleted the mga*.o files from /usr/X11R6/lib/modules/drivers and re-installed the drivers from the Matrox website, and everything is working fine again.

Strange, because the files are exactly the same as before.

Oh well.

---

### Post by simohell on 2006-05-08
[QUOTE=peaceful_dragon]OK, so I deleted the mga*.o files from /usr/X11R6/lib/modules/drivers and re-installed the drivers from the Matrox website, and everything is working fine again.
[/QUOTE]

What I did was just the same thing. Deleted and recopied.

---

### Post by timw on 2006-05-09
Yeap, that did the trick! 

Thanks guys!

---

