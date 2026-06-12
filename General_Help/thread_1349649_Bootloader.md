---
title: "Bootloader"
date: 2009-12-08
forum: General Help
---

### Post by mikemikemike on 2009-12-08
Today all the sudden, everytime I restart Ubuntu I get sent to the Grub Bootloader instead of being automatically sent to Ubuntu. How do I fix this?

---

### Post by mikemikemike on 2009-12-08
I found a screenshot.  I end up at this screen each time and have to hit enter. I want it to jsut auto go through it like it was.
[IMG]http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png[/IMG]

---

### Post by oldfred on 2009-12-08
You still are booting 7.10? That uses old grub and you can edit menu.lst

Backup - just incase
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
edit
gksudo gedit /boot/grub/menu.lst

You should see an entry like this:
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

Adjust timeout to what ever you want usually 3 is a good number.

You can also adjust how many to show with this entry:
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR=Red]2[/COLOR]

---

### Post by mikemikemike on 2009-12-08
No I have 9.10.  I just tried "  gksudo gedit /boot/grub/menu.lst " nothing is in the file.

[IMG]http://img34.imageshack.us/img34/4801/screenshotlg.png[/IMG]

---

### Post by mikemikemike on 2009-12-08
PPPLEASEE someone help! How do I get rid of this damn menu and just boot straight into Ubuntu!!!?

---

### Post by A_T on 2009-12-08
You could try installing startupmanager and see if that can help. Also maybe reinstall grub through Synaptic.

---

### Post by nomad980 on 2009-12-08
I had the same problem as you. I ended up just giving up removing grub2 and going back to grub legacy. I was actually going to make a post right now, about it.

---

### Post by oldfred on 2009-12-08
Grub2 is different than grub legacy and we all are going thru the learning curve of different ways of doing things.

You need to edit /etc/default/grub

change the hidden timeout setting:

more/better explanations here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by mikemikemike on 2009-12-08
Im not gonna lie, I'm a noob. I've messed with Linux but not enough to know what to do. So wahts the procedure for reinstalling Grub? 

I know use Synaptic Manager, but what do I do? Anyone able to give me a quick step by step?

I tried startupmanager still nothing. This is really pissing me off. If Linux has any hopes of taking over the world, it can't be so damn complicated to fix something so simple.

---

### Post by oldfred on 2009-12-08
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Or if you really want to go back to old grub for now:
HowTo: Revert from grub2 to Legacy Grub. 
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by nomad980 on 2009-12-08
oldfred:
I tried that, I am taking a stab at it and saying it has to do with that probing feature it has. I remember reading that the dev left it like that just don't remember what reason he gave. It seems to happen the second I upgrade to a new kernel.

---

### Post by mikemikemike on 2009-12-09
Edit ignore last post I fixed that. But I am still having issues with Bootloader.

---

### Post by joes7 on 2009-12-09
Install "Start Up Manager", it is the simplest tool to edit this. I had the same problem aswell , and managed to fix it using that tool. I, personally, wouldn't change the Grub menu's timeout, for one day I may need recovery mode. It's up to you.

---

### Post by mikemikemike on 2009-12-09
Ahhhh I did it. All gone. Btw joes7, I tried that it had no affect whatsoever. It does now work with Grub Legacy.


Thank you so much oldfred for the guide on how to replace Grub2 with Grub Legacy. Everything is working beautifully.



SOLVED: I used this method:   > [http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)   It is very detailed and easy to follow. Simply copy and paste the commands as you go. Just make sure when you get to the parts that say ex( hd0,2) that you put your values in. Mine was (hd0,0).

Thank you again to everyone.

---

