---
title: "Burg not applying themes after 12.04 install"
date: 2012-04-27
forum: General Help
---

### Post by Ken147 on 2012-04-27
So after I got 12.04 installed I went ahead and after much trouble got BURG reinstalled. but when I reboot my computer it is just text based BURG, no themes, it doesn't bring up the theme menu and when I press the "t" and when I press F1 no shortcuts appear. it only lets me select which OS to boot from, thats it.

I have Window 7 and Ubuntu 12.04 dual-booting on this machine.

---

### Post by zombifier25 on 2012-04-28
Actually, it you want to bring up the themes chooser, you must press 'T' (Yes, a capital T) or F2.

---

### Post by Ken147 on 2012-04-28
> **zombifier25 said:**
> Actually, it you want to bring up the themes chooser, you must press 'T' (Yes, a capital T) or F2.

the thing is I can't, I can only use the up down arrows and the c and e keys, nothing else works. :P

---

### Post by Mitchell1592 on 2012-04-29
I'm pretty sure the problem is burg is not properly installed, so grub is booting instead.
Run this to install burg,

sudo burg-install /dev/sda
then,
sudo update-burg

---

### Post by josephmills on 2012-04-29
after you have installed burg you can install burg-emu then launch burg-emu and it emulates burg for you. 

f3 is size
f2 is themes

good burg tut 
[http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/)

---

### Post by Ken147 on 2012-04-30
> **Mitchell1592 said:**
> I'm pretty sure the problem is burg is not properly installed, so grub is booting instead.
Run this to install burg,

sudo burg-install /dev/sda
then,
sudo update-burg

I have done both multiple times, burg does load but it text based not graphic.

[QUOTE=josephmills]after you have installed burg you can install burg-emu then launch burg-emu and it emulates burg for you. 

f3 is size
f2 is themes

good burg tut 
[http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/)[/QUOTE]

even in burg emu I'm not allowed to use those keys. just up down arrow e and c keys are available

---

### Post by Ken147 on 2012-04-30
> **josephmills said:**
> after you have installed burg you can install burg-emu then launch burg-emu and it emulates burg for you. 

f3 is size
f2 is themes

good burg tut 
[http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/)

I used the instructions from the link and it still does not work. same as it was before.

---

### Post by gabetheripper on 2012-08-27
I have (almost) the same problem:  I originally installed BURG under 12.04 and it worked, but after a backup-restore and re-install it is now stuck in text mode, even in burg-emu.  Very frustrating.  In other words, BUMP.

---

### Post by Xplorer4x4 on 2013-01-06
Sorry to bump this but I came here with a similar problem, burg themes not applying. So I checked the tutorial linked above. I had read over it a few times before, but when trying to change themes in burg-emu it would not take effect. The t key, non-upper case, worked fine to get to the theme menu, it just would not apply changes. Turns out I was running burg-emu as user rather then running it as sudo burg-emu. Hope it helps some one in the future.

---

### Post by Pjotr123 on 2013-01-06
Burg seems to cause problems in general.... On this forum I've read some advice not to use it, particularly not on recent hardware, because it's allegedly badly maintained.

In view of this, I advise you to remove Burg and reinstall Grub. Finally, if you want to make the Grub menu look better, you can do this: 
[https://sites.google.com/site/easylinuxtipsproject/beautifygrub](https://sites.google.com/site/easylinuxtipsproject/beautifygrub)

Good luck! :)

---

### Post by dcstar on 2013-01-06
> **Pjotr123 said:**
> Burg seems to cause problems in general.... On this forum I've read some advice not to use it, particularly not on recent hardware, because it's allegedly badly maintained.
......

Pfffftttt.

I have been using Burg without any issues at all for over two years now. I remove Grub from my systems because it is more trouble that it's worth.

---

