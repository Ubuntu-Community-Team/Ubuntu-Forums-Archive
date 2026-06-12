---
title: "ATI HD 4870 drivers and fan speed"
date: 2012-03-02
forum: General Help
---

### Post by gstaraz on 2012-03-02
I`m new to Ubuntu

Is it possible somehow to set the ATI HD 4870 1Gb fan speed to 100% in Ubuntu 11.10 (WUBI)
Currently the fan is running at less than 50% speed 

I`using the proprietary drivers [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36.3.2&lang=us&rev=10.10&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36.3.2&lang=us&rev=10.10&ostype=Linux%20x86) 

there is no control for the fan speed the Linux Catalyst cp 

______________________
- Besides that, in the system proprietis, i see that the HD4870 is running VESA 7 drivers ... is that normal ?

---

### Post by QIII on 2012-03-02
Provided it will work in a Wubi install, which it should, you will probably have to install the Overdrive version for Linux (or maybe it comes with the driver, I don't remember), which is purely command line.

When installed, you can do 

```
aticonfig --help
```

To get some guidance.

I think you need to use sudo with the following to change the fan speed

```
aticonfig --pplib-cmd "set fanspeed 0 100"
```

where 0 represents the card (0 based, so that is card number 1) and 100 is the fan speed percent.  Check that out with --help.  That is purely from memory.

Edit:  what kind of temps are you getting with the fan as it is?

---

### Post by gstaraz on 2012-03-02
Thank You very much, it worked!

How to set the code you gave me, to run automatically at system boot ? 
> aticonfig --pplib-cmd "set fanspeed 0 100"

The temp was 67 C. before I entered the code you gave me, and it worked without the "sudo"

EDIT: after few minutes the temp stabilized at 60 C. 
...It is a card that runs pretty hot

---

### Post by gstaraz on 2012-03-02
Here are the specs.

[[IMG]http://www.abload.de/thumb/ativesa3g2pg.jpg[/IMG]]("http://www.abload.de/image.php?img=ativesa3g2pg.jpg")

[[IMG]http://www.abload.de/thumb/aticpm227h.jpg[/IMG]]("http://www.abload.de/image.php?img=aticpm227h.jpg")

The VESA 7 driver ???  is it how it shold be or my card was not recognized correctly ?
..it says: Experience fallback ?!?

ps.
sorry for the dumb questions, but I just installed Ubuntu, and I have no experience with Linux :(

---

### Post by QIII on 2012-03-02
You'll probably have to write a startup script to get the fan speed adjusted at startup.  Too long to go into that in this thread.   (67 is not terribly hot under load.  My ATI BOINC projects run my 5870s up in the 70s, but that is with normal fan control by the card.)

As for VESA, do you have onboard grapics and have you set your BIOS to use PCIE as primary instead?  (Oh, never mind.  I was looking at your images on my cell phone and I looked at them again on a screen.  I'll have to do some searching on that one.)

Dumme Fragen?   So was gibt's nicht!

---

### Post by gstaraz on 2012-03-02
Thanks again for the quick reply and for your understanding 8)


Cheers,
Gianni.

---

### Post by gstaraz on 2012-03-03
To set the fan speed at system boot, I made a ".sh" file with the code that QIII gave me, checked the "allow executing as program", and loaded it in the auto start menu.

[[img]http://www.abload.de/thumb/atistartupv5cus.jpg[/img]](http://www.abload.de/image.php?img=atistartupv5cus.jpg)

Can someone tell me if this is the way to do it, as it doesn`t seems to me a very orthodox approach; but with the knowledge that I have of Linux, this is the best I came up with  :biggrin:

---

