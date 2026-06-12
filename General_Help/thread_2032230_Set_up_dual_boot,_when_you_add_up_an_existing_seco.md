---
title: "Set up dual boot, when you add up an existing second Win 7 hard drive"
date: 2012-07-23
forum: General Help
---

### Post by LeftFoot on 2012-07-23
Hi there,

Here is the drill :

-I have a 12.04 system working fine
-Add up a HD in the machine with a 7 system on it.
-I can boot from every system if I change the hard drive boot order in the bios

So now how do I modify GRUB in 12.04 so that it saw the second drive and have the chance to select which system I what to boot up.

thx 

LeftFoot

---

### Post by Mark Phelps on 2012-07-23
If, as it seems, you have each OS on its own physical drive, what I recommend is the following:
1) Set BIOS to boot from the Ubuntu drive
2) When into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB config file, adding an entry for Windows.
3) Reboot

When you reboot, you should see a GRUB menu and can select either of the OSs.

---

### Post by LeftFoot on 2012-07-23
Yes 1 physical driver per OS (makes thing so simple :) )

Just one magical command, and that's it ?!!? Awesome.

It will update the grub.cfg file ?

Thx for the help, will test that this evening.

LeftFoot

---

### Post by LeftFoot on 2012-07-26
Worked like a charm !

Now just to have to find out how to make the menu a little nicer ( = kids and wife friendly :)  )

LeftFoot

---

### Post by Mark Phelps on 2012-07-27
Which menu?  The OS selection menu put up by GRUB?

IF so, while you can add a background image (picture), that's about all the tailoring you can do with GRUB.

You should look into BURG -- it's a more GUI-like boot application.

---

