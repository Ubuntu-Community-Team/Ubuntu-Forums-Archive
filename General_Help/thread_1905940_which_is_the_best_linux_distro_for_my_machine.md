---
title: "which is the best linux distro for my machine?"
date: 2012-01-08
forum: General Help
---

### Post by iamagoodboy on 2012-01-08
Hello all!
I've been a windows user till now, and last year i installed ubuntu 10.04 cos they said ubuntu is the best linux for beginners. i want to learn linux programming and stuff, cos i have linux in my coursework this semester, and i'm a complete newbie. this is my config :
p4 2.4 ghz,
maxtor 200 gb hdd, 
intel d865gvhz motherboard,
768 mb ram,
on-board graphics.
i ran ubuntu 11.10 yesterday, and though it seems to be running fine (no lags etc), i heard it might be a strain on my machine. so what would be the best distro for my config, considering that i'm a complete newbie and i'm considering to use it full time (i have windows in my lappy, so i want to put in linux in this desktop. thanks in advance!

---

### Post by firedragoneater on 2012-01-08
Hi,
your system is probably slightly stressed under that load, Ubuntu recommend one GB of RAM +. 
So after some searching around, I think Linux Mint would be the best for you, according to one of their forums it should run OK, but the more RAM the better. Many of the heavier everyday distros now require one gig of RAM +.

If you feel that Mint is straining your machine try DSL linux or Feather linux. That would run a treat, however, I'm not sure how practical it would be for your requirements.

Hope this helps,
J.K.F

---

### Post by Paqman on 2012-01-08
> **iamagoodboy said:**
> it seems to be running fine (no lags etc)

No need to touch anything then, enjoy. If you do find it slows down a bit in use, try logging out and clicking the cog next to your username and switch the Unity-2D instead.

Mint is based on Ubuntu, it wouldn't be any lighter. Switching to a lighter desktop environment like XFCE or LXDE on Ubuntu would give better results.

---

### Post by khelben1979 on 2012-01-08
Ubuntu 11.10 should be running just fine on the pc hardware you got, and there's no reason to switch to a less heavy distribution, it's way over exaggerated in my opinion.

You will notice that the more applications you're running at the same time, that lagging becomes more and more noticeable, so if you can afford a RAM upgrade, it would do wonders with that system.

Otherwise, have a look at [XFCE]("http://en.wikipedia.org/wiki/XFCE"). It would make your system less RAM demanding without the need to change distro.

---

### Post by alenis on 2012-01-08
If you want to stay with Ubuntu, then try Lubuntu.
Otherwise I would suggest Debian with XFCE: very stable, good looking and efficient.

---

### Post by carranty on 2012-01-08
> **Paqman said:**
> Mint is based on Ubuntu, it wouldn't be any lighter. Switching to a lighter desktop environment like XFCE or LXDE on Ubuntu would give better results.

+1

Its the desktop environment that will put the most strain on your system, switching to mint or debian will have little or no effect.  ALso your PC is far too powerful to need something like DSL or feather linux.  I'd recommend XFCE over LXDE, but its down to personal choice.  Just type 
```

sudo apt-get install xubuntu-desktop
```

into a terminal, log out, then choose xfce when logging back in.

---

### Post by Sylslay on 2012-01-08
+1 for latest  XFCE or 
return to Ubuntu 10.04

You might try latest Fedora or Sabayon if You do some programing,

but the most weak in Yours PC will be
graphic card GPU, (buid in motherboard) I use myslef Intel 845 on laptop and is just ok for my needs. 
I am not able to run kde 4 + on my old intel GPU, and I still use gnome 2.30.2

Old gnome use between 300-450 MB RAM, I use for every day work ,10.04 

Freind of mine use Xubuntu 12.04 (testing alpha1) for watching HD movies on little netbook.

[http://distrowatch.com](http://distrowatch.com)

---

### Post by iamagoodboy on 2012-01-08
Hi!
Thanks all! I've decided to install 11.10 first, and then see how it performs, and if it's going to lag, then i'll go with one of the choices you guys have given me. btw will there be any difference between running it off the usb and off the hard disk after installation? thanks again. 
Regards,
Good Boy

---

### Post by Paqman on 2012-01-08
> **iamagoodboy said:**
> btw will there be any difference between running it off the usb and off the hard disk after installation? 

Yes, it'll be a lot quicker off the hard drive, and you'll be able to install the drivers for stuff like graphics cards and wifi.

---

