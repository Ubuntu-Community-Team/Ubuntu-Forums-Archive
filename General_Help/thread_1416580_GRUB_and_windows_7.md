---
title: "GRUB and windows 7"
date: 2010-02-26
forum: General Help
---

### Post by NewAuthority on 2010-02-26
I am duel-booting on a dell XPS 1530, with windows 7 as the main OS.
I installed ubuntu about 2 months after getting 7 for kicks and giggles.
I like ubuntu, but for school work I need to use windows, and I would like to change my Grub so that windows was the first system that pops up in the Grub, not the last.
I talked to a few gurus about this and they said that I needed to write a script for it.  Now I will admit, the extent of my programming is general Visual Basic, and have no idea what I need to do to get this working.  If someone could give me an example of what kind of script I would need to write, and how to do it in grub, that would be awesome.

I know it would be helpful to know what version of grub i am using, but once again, im working on becoming tech savy.  I installed ubuntu 9.1 from a live disk though if that gives any placemark on what version I have.

Any help would be appreciated!

---

### Post by theuninvitedguest on 2010-02-26
Startup Manager is the program you're looking for, it's in the repositories.

Alex

---

### Post by switch10 on 2010-02-26
+1 Startup Manager.

---

### Post by cap10Ibraim on 2010-02-26
When the grub shows you can press e to edit

---

### Post by Mark Phelps on 2010-02-26
Well ... the "gurus" you talked to need to have their titles removed :)

You don't need a script to do what you want.

Startup Manager is one way to do it if you want to avoid using the command line and editing config files.

Another way is to edit the default GRUB2 config file to change the DEFAULT string to match the GRUB menu line you always want to be the default OS on boot.

---

### Post by Aduntu on 2010-02-26
I made these same adjustments.  The thread below gave me the answers I was looking for.

[http://ubuntuforums.org/showthread.php?p=8463319#post8463319](http://ubuntuforums.org/showthread.php?p=8463319#post8463319)

---

### Post by oldfred on 2010-02-26
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry 
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

