---
title: "How to fully uninstall WINE?"
date: 2010-09-25
forum: General Help
---

### Post by calande on 2010-09-25
Hello,

I was using WINE and MS Office 2007 properly when suddenly one day MS Office stopped working properly. When saving a file, the application would crash. I decided to uninstall MS Office and to reinstall it. I wasn't able to reinstall it, the installer crashed. I then uninstalled WINE, and erased the .wine directory. I reinstalled WINE and tried to install MS Office. Same problem, the installer crashed. It's a pain not to have MS Office on this computer. Could you help me out recovering it please? What could I do to remove WINE entirely and to start over with a new clean WINE install with MS Office?
Thanks,

---

### Post by ardit ,A, on 2010-09-25
System - Administration - Synaptic Package Manager

Search for: wine

Mark for Complete Remove

Apply :D

I think you understood me :)

---

### Post by calande on 2010-09-25
This is not enough...I can't get back to the initial state with WINE fully removed somehow, even marking for complete remove. Any other idea? Thanks.

---

### Post by jongkind on 2010-09-25
You should also remove your ~/.wine folder.

---

### Post by calande on 2010-09-25
> **jongkind said:**
> You should also remove your ~/.wine folder.

I've done it already. Any other idea?
Thanks,

---

### Post by asmoore82 on 2010-09-25
There should also be some Wine related files in "~/.local/share/applications"
I can't see how they could cause a problem - but by the same token,
deleting them for a fresh start couldn't hurt.

---

### Post by calande on 2010-09-26
Thanks. I removed these application shortcuts as well. I did a complete reinstall of WINE, but when I try to reinstall MS Office again, I get the same error message from MS Office's installer: Installation failed. Could you help me please?

---

### Post by calande on 2010-09-26
I tried to install MSXLM3 with winetricks, but it won't install either. I get an error message as well: *Microsoft XML Parser setup wizard ended prematurely*.

---

### Post by gandaran on 2010-09-26
> **calande said:**
> Thanks. I removed these application shortcuts as well. I did a complete reinstall of WINE, but when I try to reinstall MS Office again, I get the same error message from MS Office's installer: Installation failed. Could you help me please?
which version of MS Office? I'm not sure if office 2007 works in wine.

---

### Post by calande on 2010-09-26
Yes, it's 2007. It used to work. 
[http://appdb.winehq.org/appview.php?appId=31](http://appdb.winehq.org/appview.php?appId=31)

---

### Post by gandaran on 2010-09-26
> **calande said:**
> Yes, it's 2007. It used to work. 
[http://appdb.winehq.org/appview.php?appId=31](http://appdb.winehq.org/appview.php?appId=31)
then the problem could be the wine version you have installed

---

### Post by calande on 2010-09-26
Thanks. I'd like to revert to the previous version. How could I do that?

---

### Post by bruno9779 on 2010-09-26
After completely removing your version of wine, you can compile it from source.

[Wine's Sourceforge page]("http://sourceforge.net/projects/wine/files/Source/") gives you versions from 0.9 to 1.3.3.

Post back if you need help compiling

---

### Post by calande on 2010-09-26
:( I'm going to try (if I have time, I have so little time). Compiling has very often lead to compilation errors on my end...

---

### Post by psycho5 on 2010-09-26
I'm running office 2007 on wine I just installed playonlinux from the website not the one from add/remove cause the website has the later version

It automatically downloads and configures the right wine version for office 2007, I can use it just fine. Give it a try

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

It'll be under Applications > Games

---

### Post by gandaran on 2010-09-26
> **calande said:**
> Thanks. I'd like to revert to the previous version. How could I do that?
from where did you install wine, did you add the wine repository to software sources or you just installed the default ubuntu wine version?
if it is the latest wine repository version you can just remove that repository and the installed wine, update the package list then install the the regular ubuntu wine version.

---

### Post by calande on 2010-09-26
Isn't that funny? I just tried to install Office again, and the installation went fine. I tried the application and it's working properly again :)
No explanation. Anyway, thanks again for the help, guys ;)

---

