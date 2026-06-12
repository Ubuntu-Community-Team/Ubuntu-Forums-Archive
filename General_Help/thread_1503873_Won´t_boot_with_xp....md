---
title: "Won´t boot with xp..."
date: 2010-06-07
forum: General Help
---

### Post by ubunxp on 2010-06-07
I have a VERY, VERY, VERY big problem...

The case is that I´ve got 2 harddisks. On the one windows xp(slave) - and on the other one ubuntu(master)

During the boot I get these errors...

"Gave up waiting for boot device"

"Boot args(cat /proc/cmdline)"

"Missing modules (cat /proc/modules; 1s , dev)"

"/dev/disk/by-uuid/f96603ce-bla bla bla does not exist"



These problems occured because of this:

After using ubuntu I tried to reset my bios, because else it couldn´t have found the disk with xp... And I didn´t disconnect the disk with xp while resetting the bios...

And now the system can´t find the disk with xp any more when booting... 

Soh...is there a way to finding the disk..?  


And I´m in doubt about IF I´ve resetted the bios at all... I miss a manual for PCCHIPS M851
May be it can take 20 minutes for the bios to be resetted..?
The shop where I bought the motherboard doesn´t exist any more... and don´t know the manufatorer

By the way......could I damage the motherboard if I tried rebooting lots of times to get it work ? 

/Ubunxp

---

### Post by Breambutt on 2010-06-07
To be frank, none of this really makes any sense. You shouldn't need to reset BIOS in order to find hard drives, and you definitely shouldn't need to clear the CMOS by removing the battery for 20 minutes (I'm assuming this is what you meant).

First of all, from within BIOS load the default settings (in case you didn't do this already). If you get the same error, see if the hard drive boot priority changed when you reset the BIOS and the boot information is on the other hard drive.

You could also try booting Ubuntu from the live CD and look around in a graphical environment.

---

### Post by ubunxp on 2010-06-07
Yes...I didn´t reset my bios just in order to find my harddisk with xp...but exactly in order to reset the settings my bios got while using the disk with ubuntu...  Because I thougt that if I resetted the bios it would forget the settings from ubuntu - and then get it possible to find the disk with xp...

I HAVE tried loading default settings in my bios...but it can´t find the disk with xp anyway... 

May be I should try to load default settings 4-5 times or more until it hopefully may find the disk..?

I can also try again to reset my bios, that means...remove the battery, move the jumper to 2 and.3. , disconnect the disks...and leave it for 5 minutes with power on...

---

### Post by Breambutt on 2010-06-07
So you don't see any mention of the other hard drive anywhere in BIOS?

Sounds like it's either broken or a cord is loose. Try removing all the cables going to the hard drive and put them back in, it's funny how often this solves mysterious hardware problems.

In any case reseting BIOS doesn't help.

---

### Post by ubunxp on 2010-06-07
I´m just wondering how a resetting itself can damage a harddisk, if that´s really so...?  

My disk has worked perfectly... And the other times I went from ubuntu to xp, I could boot my xp after resetting my bios...

---

### Post by oldfred on 2010-06-07
Do you have IDE drives or a mix of IDE & SATA. Some systems seem to come up slower than the system now boots.

Try this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Another solution I saw was just putting delay into the grub file to make it boot slower.

---

