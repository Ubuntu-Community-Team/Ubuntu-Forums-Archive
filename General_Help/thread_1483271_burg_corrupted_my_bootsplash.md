---
title: "burg corrupted my bootsplash"
date: 2010-05-14
forum: General Help
---

### Post by rudeboyskunk on 2010-05-14
I installed burg because I like the way it looks better than putting a simple splash image behind GRUB.

Anyway, somehow now my default Ubuntu 10.04 bootsplash image is corrupted, with green nastiness around the "ubuntu" part and the little red/grey dots underneath.  It looks like I'm booting into Windows 95 safe mode with 256 colors.

Any ideas?

---

### Post by iNaitvad on 2010-05-14
Hi, i hope this helps you. I installed burg recently and I have several problems, but in the end i manage to solve everything so far. 
First I belive your problem is because burg change the resolution of your bootsplash or maybe the color depth. You can change this settings on the BURG configuration file, but remeber always to update it with: ```
sudo update-burg
```
edit the config file with this: ```
gksu gedit /etc/default/burg
```
then make an update.
This variables may help you
[http://code.google.com/p/burg/wiki/ConfigurationVariables](http://code.google.com/p/burg/wiki/ConfigurationVariables)
```
GRUB_GFXMODE

Value: graphic mode screen resolution Default: 640x480 
```
The default is 640x480, i change it to 1024x768 (my old crappy crt monitor) i think you can put the color depth like this: ```
1024x768@16
``` I dindt put the color depth because it just didnt work with 32 bit color depth, so i leave it with the resolution only.

you can check this site also:
[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

Hope it helps and sorry for my crappy english... by the way I added after GRUB_GFXMODE the line GRUB_GFXPAYLOAD_LINUX with the same parameters...

---

### Post by rudeboyskunk on 2010-05-14
Ok, being able to change the resolution certainly makes it more attractive (the 640x480 made me vomit), but the bootsplash still has nasty green around the ubuntu logo while it's loading.

---

### Post by Cenotaph on 2010-05-14
If you're using the nvidia proprietary driver the GRUB_GFXPAYLOAD_LINUX command is essential and make sure its 32bit color depth.

The /etc/default/burg should have two lines like this (e.g. if your monitor ideal resolution is 1680x1050):

GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050x32

There is of course the possibility that your card doesnt support the best resolutions in grub and bootup, to see what modes your card supports press c while in grub2's menu and type 'vbeinfo' (burg should also work but i had problems using this command in burg).

---

### Post by rudeboyskunk on 2010-05-16
I'm using an ATI card, and when I typed vbeinfo in before it spouted out a bunch of stuff I didn't understand.

---

### Post by RainEverAfter on 2010-06-13
Woohoo, glad I found this thread!!!

When I saw BURG in OMG!Ubuntu! I quickly installed it and after restarting; got some resolution issues with the BootLoader (which was fixed the same day) but I've been having resolution issues with the BootSplash on my LinuxMint 9 (nVidia) for a few days until I saw this thread.

My issue has been resolved and just want to thank those who posted, keep it up!

---

