---
title: "Grub: trying to fix system that used to dual boot"
date: 2011-12-11
forum: General Help
---

### Post by LadySapphira on 2011-12-11
I'm trying to fix a system that was partitioned to dual boot ubuntu and windows xp.  I deleted all ubuntu partitions, hoping to let windows recovery function(i'm going to format afterwards and dual boot ubuntu again)




on startup, my computer is still looking for grub

"no partition found: grub"  my computer used to start up like a normal xp.. what am I missing?




ps: XP pro edition, comes with a recovery partition but no recovery CD so I can't work things that way.

---

### Post by searchfgold6789 on 2011-12-11
You'll have either reinstall grub with just Windows XP, using [BootRepair]("https://help.ubuntu.com/community/Boot-Repair"), (you can set the timeout to 0 and you won't notice a boot menu or anything) or find a Windows XP Installation disk and repair it from the Recovery console.

---

### Post by LadySapphira on 2011-12-11
I can't get anything to load, can not access windows xp


this sounds dumb but how do I get to boot repair?  at startup, I get the options for F2 of  F12.  F12 gets me boot manager/menu:

1. hdd
2. fdd
3. CD/DVD
4. LAN
5. USB memory

F2 gets me a more indepth setup utility which includes the boot menu.


I can't find another way of getting to anything, other than to run by ubuntu CD and "try ubuntu" to look at the partitions etc.




thank you so much for your help!



as far as an installation disc - would I be able to find a free one? =X that would still be supported and legal ... already paid for my computer to have XP on it


oh yes, if I select anything but CD pretty much I get
error: no such partition
grub rescue>

---

### Post by spiky001 on 2011-12-11
There are a few options try super grub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) Or here [http://www.bootdisk.com/popfiles.htm](http://www.bootdisk.com/popfiles.htm)

---

### Post by searchfgold6789 on 2011-12-11
[LIST=1]
[*]Grab your Ubuntu install CD and Try It.
[*]Once it loads, Open up a Terminal.
[*]Visit the link I gave you and follow the instructions, copying and pasting the commands into the terminal.
[*]Reboot.
[/LIST]
You won't be able to get a free Windows XP disk, legally.

No such thing as a dumb question.
 - search

---

### Post by spiky001 on 2011-12-11
You also said in 1st post you was going to reinstall again why not just reinstall again

---

### Post by LadySapphira on 2011-12-11
thanks.  will take a look and let you know how it goes either way, I think this is a bit over my head =)

---

### Post by LadySapphira on 2011-12-11
I want to reinstall again, but after I fix my windows partition.  I want to reset it to factory settings.  With ubuntu running next to it, windows could not work - the recovery partition didn't recognize its partner windows partition.

---

### Post by spiky001 on 2011-12-11
> **LadySapphira said:**
> , I think this is a bit over my head =)

Not really

---

### Post by LadySapphira on 2011-12-11
sorry, but can't find boot-repair.  either it's not on in the included CD or I'm doing something wrong (tried via terminal, software center)

I am amazed with the new CD when I originally dual booted ubuntu was much newer and I had to partition everythingmyself.  I'm going to get ubuntu and try for some other fixes you two suggested - in order to burn CD's sadly I need to use my own computer which means ubuntu needs backon.



thanks... this does help with what to look for.  Will keep updated,

> **searchfgold6789 said:**
> [LIST=1]
[*]Grab your Ubuntu install CD and Try It.
[*]Once it loads, Open up a Terminal.
[*]Visit the link I gave you and follow the instructions, copying and pasting the commands into the terminal.
[*]Reboot.
[/LIST]
You won't be able to get a free Windows XP disk, legally.

No such thing as a dumb question.
 - search

---

