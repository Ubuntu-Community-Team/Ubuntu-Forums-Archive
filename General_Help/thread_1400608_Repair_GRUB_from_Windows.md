---
title: "Repair GRUB from Windows"
date: 2010-02-07
forum: General Help
---

### Post by TriadHonor on 2010-02-07
Well, people, as many of **WUBI** user I experience a **GRUB** bug.
After some guide readed and some method tryed I found a simply solution, so I'll explain you how to fix the bug from Windows.

Just read my guide and download the file if you need it, I attack it here.
The same guide is also in a Readme inside the **ZIP** I attached.

[ATTACH]146309[/ATTACH]
( Obviusly no virus found, scanned with Avira )
------------------------------------

**---HOW TO RESOLVE THE WUBI 9.10 GRUB TROUBLES**


Most of **Wubi 9.10** installations are not fully compatible with Windows **MBR** and, specially on **Vista** and **7**, happens that WIndows take away a part of the Wubi loader, so your Karmic stop to load.

You can't use the **normal grub recovery tool** or **Ubuntu Live CD** because with Wubi **_you don't have a partition with Linux installed_**, so all the method who involve to work with a partition don't work.

Also most of the time the long way **chkdsk -l** from Windows don't work, specially with **Vista** and **7** again.
The _**defrag is unusefull**_ so don't waste your time.

The solution for this trouble is very simply, and you don't need to reinstall your Wubi, just follow this little guide.

You must know that the broken things is just the file "**wubildr**" so you need a working one **attached to this guide**, also you can **copy it from a friend** with a working Wubi or **from another working installation**, so:


**1-** Get a working "**wubildr**" here or from a friend or another working installation
**2-** Find your "**wubildr**", usually it is in **C:** or **where you installed Wubi**
**3-** Replace the broken "**wubildr**" with the one you get at point 1

**4-** Restart the PC, load Wubi and** _enjoy your life_ :popcorn:**


Guide by [B]TriadHonor
[/B]------------------------------------

Also SourceForge has a guide on this:[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by presence1960 on 2010-02-07
> **TriadHonor said:**
> Well, people, as many of **WUBI** user I experience a **GRUB** bug.
After some guide readed and some method tryed I found a simply solution, so I'll explain you how to fix the bug from Windows.

Just read my guide and download the file if you need it, I attack it here.
The same guide is also in a Readme inside the **ZIP** I attached.

[ATTACH]146309[/ATTACH]
( Obviusly no virus found, scanned with Avira )
------------------------------------

**---HOW TO RESOLVE THE WUBI 9.10 GRUB TROUBLES**


Most of **Wubi 9.10** installations are not fully compatible with Windows **MBR** and, specially on **Vista** and **7**, happens that WIndows take away a part of the Wubi loader, so your Karmic stop to load.

You can't use the **normal grub recovery tool** or **Ubuntu Live CD** because with Wubi **_you don't have a partition with Linux installed_**, so all the method who involve to work with a partition don't work.

Also most of the time the long way **chkdsk -l** from Windows don't work, specially with **Vista** and **7** again.
The _**defrag is unusefull**_ so don't waste your time.

The solution for this trouble is very simply, and you don't need to reinstall your Wubi, just follow this little guide.

You must know that the broken things is just the file "**wubildr**" so you need a working one **attached to this guide**, also you can **copy it from a friend** with a working Wubi or **from another working installation**, so:


**1-** Get a working "**wubildr**" here or from a friend or another working installation
**2-** Find your "**wubildr**", usually it is in **C:** or **where you installed Wubi**
**3-** Replace the broken "**wubildr**" with the one you get at point 1

**4-** Restart the PC, load Wubi and** _enjoy your life_ :popcorn:**



edit: wrong thread

---

### Post by Leppie on 2010-02-07
you might want to give credit to [meierfra.]("http://ubuntuforums.org/member.php?u=552151"), the owner of the sourceforge wiki page and a well respected member of this community.

---

### Post by bapoumba on 2010-02-07
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169)
In particular: [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/194](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/194)
And: [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) for the wubldr file.

This is not your work, TriadHonor, it seems to me. Thread closed.

---

