---
title: "Install without pre-existing OS?"
date: 2010-08-21
forum: General Help
---

### Post by Neverbintu on 2010-08-21
Hi everyone, I have a complete newb question.

I want to install Ubuntu on a PC and have just started reading the Ubuntu pocket guide.

All the install options seem to require a pre-existing OS ("dual mount" and so on).

But I want to install Ubuntu on a new PC and especially do not wish to pay the Microsoft Windows license fee. I want Ubuntu to be the only OS on the box.

How can I do this? Thanx in advance.

Please don't hate me for being such a total newb. :p

---

### Post by spiky001 on 2010-08-21
just insert the cd make sure bios is set to boot from cd then follow install instructions

---

### Post by Neverbintu on 2010-08-21
> **spiky001 said:**
> just insert the cd make sure bios is set to boot from cd then follow install instructions

Wow! Spiky, thanks very much for the quick and helpful reply. :D

---

### Post by sidzen on 2010-08-21
Download and burn to CD (at no more than 8X) the utility** SystemRescueCD** from Sourceforge.net (I recommend 1.3.4 or 1.3.5) here:  [http://sourceforge.net/projects/systemrescuecd/files/](http://sourceforge.net/projects/systemrescuecd/files/)

If hard drive has or has had anything at all on it, ensure a _clean install_ by using the above -- 

boot it, hit F2; either at prompt or after typing "wizard" or "startx" and getting the yellow-colored terminal, enter on the command line [PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]once it is done (rate of wipe with zeros varies, but is about 30min per 80GB or less), and you will know this by a text readout that ends in something like* xxxMB/sec*, simply type [PHP]gparted[/PHP] in the terminal after starting X if you have not already done so, and begin the partitioning process.

Have fun!!

Edit:  I take it your new PC has some OS pre-installed, correct?  If so, please wipe with zeros to ensure a trouble-free *(i.e*. pane-free) linux experience!

---

### Post by Neverbintu on 2010-08-21
Sidzen, thanks very much for the info. I plan to buy a new PC (preferably one without Windows pre-loaded) so clean install should not be necessary.

---

### Post by The Thunder Chimp on 2010-08-21
> **Neverbintu said:**
> Sidzen, thanks very much for the info. I plan to buy a new PC (preferably one without Windows pre-loaded) so clean install should not be necessary.

I heard Dell has a few computers with Ubuntu preloaded.
I switched to Ubuntu in December, and I never bought a GUI book, because it's really self-explanatory. Just burn the ISO image as explained above, and follow the instructions.

By the way, I've been here for a while now (since December on my old account), and I have never seen someone who wasn't respectful, besides one spammer in April. Please don't be afraid to ask questions.


> **sidzen said:**
> Download and burn to CD (at no more than 8X) the utility** SystemRescueCD** from Sourceforge.net (I recommend 1.3.4 or 1.3.5) here:  [http://sourceforge.net/projects/systemrescuecd/files/](http://sourceforge.net/projects/systemrescuecd/files/)

If hard drive has or has had anything at all on it, ensure a _clean install_ by using the above -- 

boot it, hit F2; either at prompt or after typing "wizard" or "startx" and getting the yellow-colored terminal, enter on the command line [PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]once it is done (rate of wipe with zeros varies, but is about 30min per 80GB or less), and you will know this by a text readout that ends in something like* xxxMB/sec*, simply type [PHP]gparted[/PHP] in the terminal after starting X if you have not already done so, and begin the partitioning process.

Have fun!!

Edit:  I take it your new PC has some OS pre-installed, correct?  If so, please wipe with zeros to ensure a trouble-free *(i.e*. pane-free) linux experience!

PHP code? What does that have to do with anything?

---

### Post by The Thunder Chimp on 2010-08-21
By the way, an easier way to partition your drive (as you most probably will have to buy a computer with Windows pre-installed), is to burn your CD and boot from it. Then you select to Try Out Ubuntu. From your desktop (the Live CD Desktop) go to System>Administration>GParted Partion Editor.

Once you are done wiping your drive from there, close GParted, and launch the Ubuntu installer that should be on the Desktop.

---

