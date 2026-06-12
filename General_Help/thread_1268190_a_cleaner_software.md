---
title: "a cleaner software"
date: 2009-09-16
forum: General Help
---

### Post by Japjeev on 2009-09-16
ok so is there any registry cleaner or like temporarily files cleaner like ccleaner for ubuntu? i need one really bad my ubuntu is slowing down? thanx

---

### Post by NoaHall on 2009-09-16
There's no registry for Linux. So you don't need a cleaner. 

Although, try, run "sudo apt-get autoclean" and "sudo apt-get autoremove"

---

### Post by sunchiqua on 2009-09-16
Go to:[COLOR=DimGray] System / Administration / Computer Janitor[/COLOR] ( use carefully )[COLOR=DimGray]
[/COLOR]

---

### Post by oldsoundguy on 2009-09-16
ubuntu has no registry.

Your slow down could be many things and you need to see if it is on or off line .. on line can be your ISP

But .. this will clean it up (for what it's worth): (follow the instructions!)

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by fooman on 2009-09-16
bleachbit is a great app for cleaning up temp files and the like...i believe its in the universe repos.

i seriously doubt it will help speed your computer up.  that is more likely do to some other issues.

---

### Post by oldos2er on 2009-09-16
/tmp is cleared on a reboot.

---

### Post by ajgreeny on 2009-09-16
As a previous post says, be very, very careful with Computer janitor, as it will possibly/probably suggest you remove a few applications that you do want to keep. I don't think it will make any difference to the speed of your system, however, and suggest it must be something else that is the cause.

Use ```
top
``` to see if anything is hogging cpu or memory usage.

---

### Post by Andrew.Z on 2009-09-17
> **NoaHall said:**
> There's no registry for Linux.

[Linux does have a registry (many of them)](http://bleachbit.blogspot.com/2008/12/linux-registry-cleaner-myth.html), but no, removing the files in the article probably won't speed things up.

---

### Post by scouser73 on 2009-09-17
+1 for [[COLOR="Red"]**BleachBit**[/COLOR]]("http://bleachbit.sourceforge.net/"), which can be found in the repositories.

---

### Post by Andrew.Z on 2009-09-17
> **scouser73 said:**
> +1 for [[COLOR="Red"]**BleachBit**[/COLOR]]("http://bleachbit.sourceforge.net/"), which can be found in the repositories.

BleachBit 0.3.1 in the Ubuntu 9.04 repository is old and buggy.  Please use a newer version such as 0.6.4 (.deb available from the link above).

---

### Post by mcduck on 2009-09-17
> **Andrew.Z said:**
> [Linux does have a registry (many of them)](http://bleachbit.blogspot.com/2008/12/linux-registry-cleaner-myth.html), but no, removing the files in the article probably won't speed things up.

When people say that Linux doesn't have a registry they usually mean that Linux doesn't have a registry in the way Windows does, a single, massive, binary file that stores information about everything including your apps, settings, and the system itself, and that would grow and grow and cause the system to slow down over time.

Of course it doesn't meant that individual applications wouldn't have their own registries or databases. :)

---

### Post by Andrew.Z on 2009-09-17
> **mcduck said:**
> When people say that Linux doesn't have a registry they usually mean that Linux doesn't have a registry in the way Windows does, a single, massive, binary file that stores information about everything including your apps, settings, and the system itself, and that would grow and grow and cause the system to slow down over time.

Of course it doesn't meant that individual applications wouldn't have their own registries or databases. :)

Yes, and it's also true that the Linux's registries accumulate orphaned records which can be cleaned up.  I think there could be a small performance penalty for some of these orphans, but generally it is small.  Even in Windows on slow machines I haven't witnessed registry cleaning speed the system up.

---

### Post by DjBones on 2009-09-17
Although I don't suggest it without knowing what all the services and daemon's do, but you can install sysvconfig:
```
sudo apt-get install sysvconfig
```
It's a command line utility to help you change your init scripts.  You can use it to stop some services that you don't need (say, CUPS if you don't have a printer) from starting and thereby using resources.  Preferable to removing the applications in my opinion, but if you halt something integral to the system it might not function properly.

---

### Post by scorp123 on 2009-09-17
> **Andrew.Z said:**
> Linux does have a registry  No, it doesn't. Gnome being the only stupid exception. What they list there on that site are local config files inside your $HOME directory that you could easily remove yourself if you bothered to look for them. Nothing against that "cleaner" software, but _PLEASE_ don't call simple config files "registries". Those plain-text config files have nothing in common with Micro$oft's binary format registry (*.REG) files in any way.

---

### Post by NoaHall on 2009-09-17
> **Andrew.Z said:**
> [Linux does have a registry (many of them)](http://bleachbit.blogspot.com/2008/12/linux-registry-cleaner-myth.html), but no, removing the files in the article probably won't speed things up.

Haha. You're funny. Linux may have config files, and the system might be all linked up(which is needed), but there is no registry. A registry is something that Windows alone has(as far as I know, there are no other OS's with it, exception being perhaps ReactOS). Linux doesn't have it. They are different operating systems. That's like saying  a cow has four legs so a horse is also a cow because it too has four legs.

---

### Post by Andrew.Z on 2009-09-17
> **scorp123 said:**
> No, it doesn't. Gnome being the only stupid exception. What they list there on that site are local config files inside your $HOME directory that you could easily remove yourself if you bothered to look for them. Nothing against that "cleaner" software, but _PLEASE_ don't call simple config files "registries". Those plain-text config files have nothing in common with Micro$oft's binary format registry 

Who says a registry has to be binary?  WINE implements the Windows registry APIs and stores the data as text files.  Is that a registry?

> (*.REG) files in any way.

.reg files are text files (exported from the registry as backups for importing back in to the registry).

> **NoaHall said:**
> Haha. You're funny. Linux may have config files, and the system might be all linked up(which is needed), but there is no registry. A registry is something that Windows alone has(as far as I know, there are no other OS's with it, exception being perhaps ReactOS). Linux doesn't have it. They are different operating systems. That's like saying  a cow has four legs so a horse is also a cow because it too has four legs.

I didn't say, "Linux is Windows."  I claimed Linux has multiple systems for registering shortcuts, file associations, etc.  Does Linux have a well-defined system for registering shortcuts and file associations?

---

### Post by scorp123 on 2009-09-17
> **Andrew.Z said:**
> Who says a registry has to be binary?  If it isn't binary then it isn't a "registry" but a mere plain-text ***config file***. That's how we call things here, OK? :D

> **Andrew.Z said:**
>  WINE implements the Windows registry APIs and stores the data as text files.  Is that a registry?  No. Still just a config file.

> **Andrew.Z said:**
>  .reg files are text files (exported from the registry as backups for importing back in to the registry).   I don't give a sh** because I have quit Windows in 1996. "Registry == binary Windows crap" is all I need to know about that. And something like this certainly doesn't exist on Linux or I would have noticed in the past 13 years or so. ;)

Please call config files what they are: "config files". And not "registries".

---

### Post by scorp123 on 2009-09-17
> **NoaHall said:**
> as far as I know, there are no other OS's with it IBM AIX (and yes, it's a commercial UNIX variant and yes, it has a registry similar to Windows!)

[http://www.unix.com/aix/68510-how-see-registry-aix.html](http://www.unix.com/aix/68510-how-see-registry-aix.html)
[http://support.apple.com/kb/TA36311?viewlocale=en_US](http://support.apple.com/kb/TA36311?viewlocale=en_US)
[http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.genprogc/doc/genprogc/odm_cmds_subrs.htm](http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.genprogc/doc/genprogc/odm_cmds_subrs.htm)

This explains the acronym some people use for AIX = [COLOR="Red"]Ai[/COLOR]n't Uni[COLOR="Red"]x[/COLOR]

I have never had the pleasure so far to use AIX ...

---

