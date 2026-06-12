---
title: "problems!!!!!!!! :("
date: 2012-06-20
forum: General Help
---

### Post by himanee on 2012-06-20
hello everybody,

again i am in a problem and this time i don't know what is the title of my problem! :(

so chronological background is as below;

[LIST]
[*]my dell inspiron laptop was dropped by me accidentally when i was working in windows 7(i have both ubuntu and windows7)
[*]windows 7 stopped starting, its just takes shows login page and then does nothing even after entering the password(the problem is not yet resolved n i want resolve that too, but officially i cant ask for it here)
[*]i was using ubuntu system (karmic) only(windows not working) for many days/months. during that time i tried to upgrade ubuntu to 10.04 (something lynx?). unfortunately due to some power and other problems it was interrupted twice! :(
[*]to recover windows i inserted winows recovery cd and instantly remembered that i had been through disaster due to that earlier, so aborted it.
[*]after that ubuntu was not starting, so i ran recovery on ubuntu and following the instructions successfully upgraded it to 10.04
[*]but it still shows some errors which i am not able to clear. below i am giving various errors shown by the ubuntu system (old and new) during all these events
[*]1] an upgrade from "lucid" to "karmic" isnot supported with this tool
2] Not all updates can be installed. run a partial upgrade to install *** many updates as possible
3]:/var/cache//apt/archives/kdebase-runtime-data_4%
3a4.4.5-0ubuntu1.1_all.deb trying to overwrite '/usr/share/kde4/apps/khelpcenter/searchhandlers/docbook.
desktop', which is also in package khelpcenter 4 4
4] errors were encountered while processing:
  kdebase-runtime-data-common
libmono-security2.0-cil
5]an error occured please run package magr from right click menu or apt-gate in a terminal to see what is 
wrong the error msg was
6]Error: BrokenCount > 0 this usually means that your installed packages have unmet dependencies
could not install adobe-flashplugin
process installed preremoval script returned error exit status 2
[/LIST]


PLEASE HELP ME SOMEBODY AS ALWAYS BEEN.


thanks in advance.
himanee.

---

### Post by wilee-nilee on 2012-06-20
Can you consolidate that wall of text to what is actually happening right now.

I doubt you wil get much help here, the header has no reference to the problem, and all I see is a wall of text.

---

### Post by mastablasta on 2012-06-20
you could try to do a fresh install.
 
are you using KDE (kubuntu)? if so then i suggest you try to do fresh install of 12.04 since it has a newer and more stable KDE interface.

---

### Post by F104G on 2012-06-20
> **himanee said:**
> 
[LIST]
[*]1] an upgrade from "lucid" to "karmic" is not supported with this tool
[/LIST]
 Lucid was released AFTER Karmic, so I'm guessing an "upgrade" from a newer to an older version wouldn't be possible with any tool.  Ubuntu releases are named alphabetically, the current version is called "Precise".

---

### Post by black veils on 2012-06-20
your problems started after you dropped the laptop?  surely the reason is because the harddrive is damaged ?

---

### Post by xp15 on 2012-06-20
it will be more easyer if you'll install ubuntu 12.04 and then we'll see what happens.
and again-if the harddrive is damaged-you may backup what uoy can and replaced it with a better one.

---

### Post by himanee on 2012-07-03
[LIST]
[*]my current problem is i am not able to install flash player or any other plugin. can't watch any videos on internet.
[*]on the desktop, at the uppermost-right corner(near bluetooth and connectivity symbols) some error symbol/notification is shown which says;
[/LIST]
***an error occured please run package manager from right click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0' this usually means that your installed packages have unmet dependencies***

[LIST]
[*]i know that karmic is before lucid and that is why i was surprised to see that message while upgrading from karmic to lucid.
[*]when i run the package manager and start partial upgrade, after a while it shows the following error;
[/LIST]
[I][B]Could not install 'adobe-flashplugin'

The upgrade will continue but the 'adobe-flashplugin' package may not be in a working state. Please consider submitting a bug report about it.
subprocess installed pre-removal script returned error exit status 2

[/B][/I]
[LIST]
[*]now how do i install ubuntu 12.04? i have windows7 in one partition( which is not working currently although).
[/LIST]
i hope my problem now and somebody will be abl to help.
thanks n regards,
himanee.

---

### Post by himanee on 2012-07-03
following was also popped;
[I][B]sorry, the adobe-flash plugin could not be installed report the problem
[/B][/I]
and one more error regarding adobe-flash plugin had occurred which i missed to copy here.

---

### Post by mastablasta on 2012-07-03
> **himanee said:**
> 
[LIST]
[*]now how do i install ubuntu 12.04? i have windows7 in one partition( which is not working currently although).
[/LIST]Select Install on boot and then chose manual aprtitioning and simply point the root partition to your existing root. This will overwrite the current install.
 
another option is to erase current install (i.e. format disk on install). but make sure you format the Ubuntu partition only ;)

---

### Post by mastablasta on 2012-07-03
> **himanee said:**
> following was also popped;
***sorry, the adobe-flash plugin could not be installed report the problem***
 
and one more error regarding adobe-flash plugin had occurred which i missed to copy here.
 
 
regarding flash once you perform a fresh install you can simply install restricted extrass package which will also install many other goodies besides flash (such as mp3 decoding etc.)

---

