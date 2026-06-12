---
title: "dual booting and windows installed last, how do I get grub back?"
date: 2010-01-08
forum: General Help
---

### Post by ozguitarplayer on 2010-01-08
Hi,
For work reasons I need to install windows7 ...oh the shame of it!
 
I am already running Jaunty Jackalope and Lenny as dual boot.
I'm concerned that I will not be able to boot into either Linux system after I install windows as I will loose grub.
How can I overcome this?
Is it possible to reassign boot using GParted?

---

### Post by blur xc on 2010-01-08
I installed Vista after an Ubuntu install and I had to reinstall grub from the live cd. 

I followed instructions from this website: [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

I don't see one for a linux/win7 dual boot w/ linux installed first...

I'm curious for the answer as well, because I can see myself in the near future doing this same thing...

BM

---

### Post by oldfred on 2010-01-08
You will need to use a liveCD and follow the commands in this:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Follow the instructions for grub legacy. You should see two listings when you search for grub, just know which partition has the install that you want to use for booting. Since it is grub legacy you may have to manually add the win entry to menu.lst.

Be sure to create a primary partition for windows.

---

### Post by adam814 on 2010-01-08
It *should* be about the same as for Vista.  As far as installing grub goes it's the same procedure no matter what other OS might be on the drive.

I should warn you though that the guide blur xc links to assumes you're using legacy grub.  As of Ubuntu 9.10 this is no longer the case.  So if you're installing an older version you should be fine following it directly.  If you're planning on installing Karmic see here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by ozguitarplayer on 2010-01-09
Thanks everyone for the replies, as yet I haven't installed windows7 I just needed to know if it was possible to do it first. The install will happen soon and I'll reply after I've tried it out.

---

