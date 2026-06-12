---
title: "boot error no such device : a77318a7-5f3d-4531-8d27-370f2b43c0e2"
date: 2010-02-07
forum: General Help
---

### Post by frodriguez96 on 2010-02-07
Help me Please,
when i turn on my computer it says : 
error : no such device : a77318a7-5f3d-4531-8d27-370f2b43c0e2
Failed to boot default entries

Please tell me how to fi it and whats wrong.

             -FRodriguez96

---

### Post by frodriguez96 on 2010-02-07
help please

---

### Post by frodriguez96 on 2010-02-07
anyone please help me
i need help now or as soon as possible

---

### Post by m4nm4n on 2010-02-07
Go here: [http://ubuntuforums.org/showpost.php?p=8755145&postcount=23](http://ubuntuforums.org/showpost.php?p=8755145&postcount=23)

---

### Post by drs305 on 2010-02-07
If you can get to the Grub 2 menu, you can boot by highlighting your normal Ubuntu partition, pressing "e", removing the "search" line by holding down the DEL key, and changing the "linux" line part which refers to ..."root=UUID=<long number>..." to ..."root=/dev/sdXY" (such as sda1, sda5, etc). 

You will need to know what partition your Ubuntu install is on. If it's on your first drive, it is normally going to be sda1 or sda5.

The link can probably get you to the Desktop but is not a long-term solution as it edit's grub.cfg, which will be overwritten the next time grub is updated.

Once you can boot, run this boot info script and we can tell you how to permanently fix your files.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by frodriguez96 on 2010-02-07
> **m4nm4n said:**
> Go here: [http://ubuntuforums.org/showpost.php?p=8755145&postcount=23](http://ubuntuforums.org/showpost.php?p=8755145&postcount=23)thanks:popcorn:

---

### Post by frodriguez96 on 2010-02-07
> **drs305 said:**
> If you can get to the Grub 2 menu, you can boot by highlighting your normal Ubuntu partition, pressing "e", removing the "search" line by holding down the DEL key, and changing the "linux" line part which refers to ..."root=UUID=<long number>..." to ..."root=/dev/sdXY" (such as sda1, sda5, etc). 

You will need to know what partition your Ubuntu install is on. If it's on your first drive, it is normally going to be sda1 or sda5.

The link can probably get you to the Desktop but is not a long-term solution as it edit's grub.cfg, which will be overwritten the next time grub is updated.

Once you can boot, run this boot info script and we can tell you how to permanently fix your files.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) english please i didnt get you please make it easier

---

### Post by frodriguez96 on 2010-02-07
if i see a mouse on th screen what does it mean ?

---

### Post by drs305 on 2010-02-07
For this procedure, you will need to know what partition your Ubuntu installation is on. If it's on the first drive, first partition, it is sda1. If it's on the first drive, 5th partition, it would be on sda5. Second drive, first partition: sdb1, etc.  If you don't know, at the Grub menu press "c" and then type "ls" at the prompt. It will return the drives/partitions Grub sees (hd0, hd0,1), etc. If you still don't know what partition Ubuntu is on, provide us with the results of the "ls" command and tell us if you are using Windows.

If you can boot and see the Grub 2 menu:

Highlight the Ubuntu kernel you want to boot, using the UP/DN arrows.

Once it is highlighted, press "e"

This will display the entire menu entry code lines.

Use the arrow keys to position the cursor at the start of the line that begins with "search"

Hold down the DEL key until the entire line is deleted.

Move to the line that starts with "linux"

Use the cursor keys to move to "root=UUID=<some long number>

Change this to look like "root=/dev/sd**a1**"   Use the correct "sdXY" format based on where your Ubuntu install is (sda1, sda5, etc). **Added: If you don't know, just try booting without changing this line.**

The line should look like:
> linux /vmlinuz-<someversion> root=/dev/sd**a1** ro quiet splash 

Then CTRL-x to boot.

If you still don't understand, go to the link already mentioned, accomplish those steps, but return here so we can clean things up a bit afterward.

---

### Post by frodriguez96 on 2010-02-07
> **drs305 said:**
> For this procedure, you will need to know what partition your Ubuntu installation is on. If it's on the first drive, first partition, it is sda1. If it's on the first drive, 5th partition, it would be on sda5. Second drive, first partition: sdb1, etc.  If you don't know, at the Grub menu press "c" and then type "ls" at the prompt. It will return the drives/partitions Grub sees (hd0, hd0,1), etc. If you still don't know what partition Ubuntu is on, provide us with the results of the "ls" command and tell us if you are using Windows.

If you can boot and see the Grub 2 menu:

Highlight the Ubuntu kernel you want to boot, using the UP/DN arrows.

Once it is highlighted, press "e"

This will display the entire menu entry code lines.

Use the arrow keys to position the cursor at the start of the line that begins with "search"

Hold down the DEL key until the entire line is deleted.

Move to the line that starts with "linux"

Use the cursor keys to move to "root=UUID=<some long number>

Change this to look like "root=/dev/sd**a1**"   Use the correct "sdXY" format based on where your Ubuntu install is (sda1, sda5, etc). **Added: If you don't know, just try booting without changing this line.**

The line should look like:


Then CTRL-x to boot.

If you still don't understand, go to the link already mentioned, accomplish those steps, but return here so we can clean things up a bit afterward.
ok but what would my sdXY if i used entire hardrive ?

---

### Post by ngrieb on 2010-02-07
Thanks, the same thing happened to me. Perhaps we should report this somehow. Anyone have any idea what caused this?

---

### Post by drs305 on 2010-02-07
> **frodriguez96 said:**
> ok but what would my sdXY if i used entire hardrive ?

It should be sda1
With one hard drive, Ubuntu can normally be found on sda1 or sda5
If you use the "ls" command (by pressing c at the Grub2 menu), you should see (hd0), your hard drive, and then some additional partitions (hd0,1). If you have windows, you will probably see (hd0,1), maybe (hd0,2) and Ubuntu would normally be (hd0,5) which is sda5.

---

