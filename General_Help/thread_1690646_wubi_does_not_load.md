---
title: "wubi does not load"
date: 2011-02-18
forum: General Help
---

### Post by drewk2 on 2011-02-18
Hello,
I wanted to install Ubuntu and try it out. 
It seemed like Wubi would be the easiest way to try out Ubuntu. I went to this website to download Wubi:

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

After downloading Wubi, it tells me I have to reboot. 
However, after rebooting, my PC just restarts as normal booting up to Windows and never gives me the option to pick Windows or Ubuntu. When I go to Start, then All Programs, Wubi or Ubuntu does not show up. However, if I go to control panel, then Add/Remove programs, Ubuntu does show up taking up about 17GB of space. 
I have uninstalled and re-installed twice using Firefox, and twice using Internet Explorer and still does not boot up with the Windows or Ubuntu choice. It just boots up as normal into my Windows. 

I am running Windows XP Media Edition. 

Any ideas or help?

Thanks,
Drew

---

### Post by Rubi1200 on 2011-02-19
Hi and welcome to the forums :-)

Can you check in Windows whether the following files are at the root of the C drive (which is where I assume you chose to install):

 C:\ubuntu\disks\root.disk and C:\ubuntu\disks\boot

You can also look if these files are at the root of C:[FONT=monospace]
[/FONT]
wubildr.mbr and wubildr 

Did you make any changes to the timeout for Windows to boot by editing the boot.ini file (default is 30 seconds)?

---

### Post by drewk2 on 2011-02-20
YES,
These 2 files are at the root of C:

C:\ubuntu\disks\root.disk and C:\ubuntu\disks\boot

Yes, wubildr.mbr and wubildr are in the winboot file at the root of C. 

I did NOT make any changes to the timeout for Windows to boot by editing the boot.ini fil. 

Any other ideas to help?

---

### Post by bcbc on 2011-02-20
Check boot.ini even if you haven't modified it. In some cases the ubuntu entry fails to get added, or the timeout is set at zero. If the Ubuntu entry is there, then likely the timeout needs to be changed.

You can look in the startup & recovery settings to see this (my computer, right click, properties, advanced tab, look on the bottom for Startup & recovery.

PS it doesn't matter which browse you download wubi.exe with. It runs outside of the browser, but if you are running it more than once, you should download the Ubuntu cd image (.iso) yourself as it's quicker than letting Wubi download it so many times.

---

### Post by drewk2 on 2011-02-20
Pardon my ignorance, but how do I check boot.ini and how do I alter the timeout if it is set at zero? 
I would like it to be about 5 seconds if possible.

---

### Post by bcbc on 2011-02-20
> **drewk2 said:**
> Pardon my ignorance, but how do I check boot.ini and how do I alter the timeout if it is set at zero? 
I would like it to be about 5 seconds if possible.

You can do this from the startup & recovery settings - see my previous post

---

### Post by drewk2 on 2011-02-21
Thank you so much!
The timeout was set at 0. I set it to 10 seconds and it works perfect!

---

