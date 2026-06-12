---
title: "Switching Video Cards in 10.04/32"
date: 2010-07-17
forum: General Help
---

### Post by McRat on 2010-07-17
I set up a Ubuntu machine using the OnBoard video, and it runs OK.

Now, I put a nVidia card in it (2009'ish 512mb), and there is no screen after the BIOS screen.

If I boot off a Live CD, everything is fine, so the card is supported.

How do I get Ubuntu to look for the new card on bootup?  Do I have to reinstall?  If so, will it wipe out the installed applications and data?

Thanks!



*solution*
```

cd / (this gets you to root)
cd etc 
sudo chmod 777 X11 (this permits changing names)
cd X11
sudo chmod 777 xorg.conf.failsafe
sudo mv xorg.conf.failsafe bkxorg.conf.failsafe (this changes the name)

Now reboot.  Next:

cd / 
nivia-xconfig

Reboot again, and you should be able to use the video card.  
```

---

### Post by McRat on 2010-07-17
New info:

The card is a **MSI M452-9502 GeForce 9500 GT Video Card - 512MB DDR2, PCI Express 2.0**  User reviews indicate it works great with various Linux versions.  

The motherboard is a Gigabyte MA785GM-US2H which has onboard ATI HD4200 graphics.

I can get either Video chipset system to function with LiveCD.  But I cannot get either chipset to function with the HDD Ubuntu 10.04 installation.  Disabling the onboard graphics does not fix the problem.

So this card WORKS fine with Ubuntu on a CD.  I just need to find out where the video settings exist on a Linux machine.  Extensive searching proves that I apparently don't know how to ask the right question.

---

### Post by dcstar on 2010-07-17
> **McRat said:**
> I set up a Ubuntu machine using the OnBoard video, and it runs OK.

Now, I put a nVidia card in it (2009'ish 512mb), and there is no screen after the BIOS screen.

If I boot off a Live CD, everything is fine, so the card is supported.

How do I get Ubuntu to look for the new card on bootup?  Do I have to reinstall?  If so, will it wipe out the installed applications and data?

Thanks!

Rename the /etc/X11/xorg.conf file and reboot.

---

### Post by McRat on 2010-07-17
> **dcstar said:**
> Rename the /etc/X11/xorg.conf file and reboot.

Excellent.  I'll give that a try.:KS

---

### Post by McRat on 2010-07-18
> **dcstar said:**
> Rename the /etc/X11/xorg.conf file and reboot.

Thanks!  That got the ball rolling.

For other readers:

As far as I can tell, you need to do -

cd /            (this gets you to root)
cd etc          
sudo chmod 777 X11            (this permits changing names)
cd X11
sudo chmod 777 xorg.conf.failsafe
sudo mv xorg.conf.failsafe bkxorg.conf.failsafe (this changes the name)


Now it "sees" the nvidia card, and I can look at the screen.
It says I have the proprietary nVidia card driver installed, but if I try to access the settings I get:

```

You do not appear to be using the NVIDIA X driver.  
Please edit your X configuration file 
(just run `nvidia-xconfig` as root), 
and restart the X server.
```

No idea what an X server is, I assume it's the API for the graphics.  Hopefully they mean reboot.

Not sure what the X config file is, I'll assume it's that xorg.conf.failsafe file.

But just getting it to display anything without the CD was exciting.  It wouldn't accept the power switch or CNTL-ALT-DEL to shutdown between tries, so I had to unplug it from the wall about 50 times.

---

### Post by McRat on 2010-07-18
Next:

```


patrick@U32Blacky:~$ [COLOR="Green"]cd /[/COLOR]
patrick@U32Blacky:/$ [COLOR="green"]nvidia-xconfig[/COLOR]

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

patrick@U32Blacky:/$ 

```

Reboot, then everything WORKS!!!

Thanks.

Now the downside, the nvidia driver 195.36.24 doesn't like Wine much.  The onboard ATI chip was seriously slow, but it did not have have problems with 3D rendering or games under Wine.

Running CADKEY, the nvidia card corrupts the screen with menu artifacts when rendering, and running with Starcraft, it reduces the screen to a very small size, and the mouse barely works.

---

