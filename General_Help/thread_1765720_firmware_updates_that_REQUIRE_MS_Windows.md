---
title: "firmware updates that REQUIRE MS Windows"
date: 2011-05-23
forum: General Help
---

### Post by eltonw on 2011-05-23
I need to do [COLOR="DarkRed"]**firmware updates**[/COLOR] to various peripherals ... and may need to do so again in future. The problem is that all or most of the manufacturers provide [COLOR="Sienna"]BIOS updates are Microsoft Windows ONLY[/COLOR]. ](*,)

To that end I thought that I would install **WINE**, but I have been advised that **WINE** [COLOR="DarkRed"]does not give true access to the hardware layer.[/COLOR]

**As an alternative**, I thought of [COLOR="Sienna"][FONT="Microsoft Sans Serif"]creating a Windows "live CD"[/FONT][/COLOR].

My idea is _to create a bootable "live CD Windows" on USB stick_, so that I can boot from the memory stick, and still have access to the other hardware, either within my netbook, or attached to it. All the resources I find show how to create ***linux*** live CDs 'under Windows", not the converse.

I do have unetbootin installed, and I know it is available for the Mac. Also I *DO* have an **XP installation DVD** [NEVER USED] that came with the netbook. 

AFAIK, _an installation disk cannot be run as a "live CD"_. (Kindly correct me if I am mistaken abou this.)

TIA for any guidance or pointers....

---

### Post by sanderd17 on 2011-05-23
there are two things that you can do:

[LIST]
[*]Complain the the computer manufacturer that you need it to work without Windows, but I bed that they will send you a windows CD and say you have to install it
[*]Put another HDD in the netbook, install windows, update the bios and switch HDD's again
[/LIST]

It's nearly impossible to run windows so it can touch the hardware without installing it on the harddisk.

---

### Post by 67GTA on 2011-05-23
BartPE is a "live" Windows ISO. I have used it before to run bios and firmware updates. You just have to be sure of the name of the device your targeting and change the installer target to match. [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by sanderd17 on 2011-05-23
That's a good one. I never heard of it.

---

### Post by 67GTA on 2011-05-23
BartPE was built as a free version of the original WindowsPE. Since WindowsPE can be gotten for free, you may want to check it out too. The big difference is that WindowsPE is pretty bare. BartPE has recovery/repair applications preinstalled. [URL="http://en.wikipedia.org/wiki/Windows_Preinstallation_Environment"]http://en.wikipedia.org/wiki/Windows_Preinstallation_Environment
[/URL]

---

### Post by eltonw on 2011-05-23
> **67GTA said:**
> BartPE was built as a free version of the original WindowsPE. Since WindowsPE can be gotten for free, you may want to check it out too. The big difference is that WindowsPE is pretty bare. BartPE has recovery/repair applications preinstalled. [URL="http://en.wikipedia.org/wiki/Windows_Preinstallation_Environment"]http://en.wikipedia.org/wiki/Windows_Preinstallation_Environment
[/URL]

Before receving your comments, I came across BartPE HERE:[http://www.nu2.nu/pebuilder/]("http://www.nu2.nu/pebuilder/")
[COLOR="DarkGreen"]Bart's Preinstaller is NOT in itself an ISO but is _a utility to CREATE a Windows live CD_[/COLOR].
I do have a WinXP CD that came with my Asus EEE netbook. 
Regrettably, BartPE fails under WINE. (By that, I mean it starts to create the Windows iso image but fails with a message to check the WINE website about problems with wineconfig.):frown:
So no luck still.

WINE may be OK for running games and such, but even this means I need a real Windows machine to create the live CD. 

As for the WindowsPE, could you kindly point me to a download link?

thanks for your comments and suggestions

---

### Post by linuxinstalledfromhdd on 2011-05-23
Bart PE is what you need. Someone already did all the hardwork for you.

---

### Post by linuxinstalledfromhdd on 2011-05-23
If you do work on systems you should always have a copy of BartPE handy too.  It helps to change passwords in Windows Server if locked out.

---

