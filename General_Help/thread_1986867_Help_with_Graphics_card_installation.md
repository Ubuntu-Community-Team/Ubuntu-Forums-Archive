---
title: "Help with Graphics card installation"
date: 2012-05-25
forum: General Help
---

### Post by ScrufffyJoe on 2012-05-25
Hi :)

Recently I bought myself a Sapphire Radeon HD 6870 graphics card. I have plugged it into my machine and am currently using the card's HDMI output, but I have run into problems with Linux.


Firstly, the card's installation manual recommends I first turn off the integrated graphics in my machine before using it. I have snooped around my BIOS (I have an ASUS F1A75-M) and not managed to find anything to do this. So I put in the CD which came with the motherboard.

On this CD is two folders. an "isolinux" and a "LinuxDrivers". In the Linux drivers I have found a tar.gz file as well as a ReadMe recommending I use the latest Linux Kernel. I have found and downloaded this, it is a tar.bz2 file, but do not for the life of me know what to do with it.

If anyone can help me turn off my integrated graphics it would be greatly appreciated as I am lost.


Another problem comes with the driver installation CD of the graphics card. I cannot get this to work and am even more clueless on this. Is there any way I can get drivers for my card, because as far as I can tell the drivers on the CD only work on Windows 7.


Thanks in advance for any help :)


P.S. In the latest update how do I make it so the Launcher is hidden? It's rather annoying that it's constantly there.

---

### Post by kc1di on 2012-05-25
As far as hiding the launcher goes you do this:
go to system settings > Appearance> behavior > on the right side there is a on off type switch turn on auto hide with that. 

the panel will hide when not in use. here is a you tube presentation of how to install the catalyst drivers for you graphics card- AMD/ATI cards are hard to do in linux but it can be done. 
[http://www.youtube.com/watch?v=U1kanjD4qgo]("http://www.youtube.com/watch?v=U1kanjD4qgo")

As far as turning off the on board graphics card there should be a bios setting that will do that.

---

### Post by kanikilu on 2012-05-25
> If anyone can help me turn off my integrated graphics it would be greatly appreciated as I am lost.

It's in the manual (section 2-19), under Advanced Menu -> Onboard Devices.

[http://support.asus.com/download.aspx?SLanguage=en&p=1&s=41&m=F1A75-M&os=&hashedid=dU6PPKrFyG7V4pwS](http://support.asus.com/download.aspx?SLanguage=en&p=1&s=41&m=F1A75-M&os=&hashedid=dU6PPKrFyG7V4pwS)

---

### Post by ScrufffyJoe on 2012-05-25
> **kc1di said:**
> As far as hiding the launcher goes you do this:
go to system settings > Appearance> behavior > on the right side there is a on off type switch turn on auto hide with that. 

the panel will hide when not in use. here is a you tube presentation of how to install the catalyst drivers for you graphics card- AMD/ATI cards are hard to do in linux but it can be done. 
[http://www.youtube.com/watch?v=U1kanjD4qgo]("http://www.youtube.com/watch?v=U1kanjD4qgo")

As far as turning off the on board graphics card there should be a bios setting that will do that.Ok, thanks. Managed to find the drivers and I am trying to download them right now (suffering connection issues >.<). I'll definitely follow that video to install the drivers.

I'll look in the BIOS again but I couldn't find anything the first time.

---

### Post by ScrufffyJoe on 2012-05-25
> **kanikilu said:**
> It's in the manual (section 2-19), under Advanced Menu -> Onboard Devices.

[http://support.asus.com/download.aspx?SLanguage=en&p=1&s=41&m=F1A75-M&os=&hashedid=dU6PPKrFyG7V4pwS](http://support.asus.com/download.aspx?SLanguage=en&p=1&s=41&m=F1A75-M&os=&hashedid=dU6PPKrFyG7V4pwS)Ok, thank you. I've found the option. Still have one question though. The options for integrated graphics are "Auto" and "Force". Which one of these will actually disable the integrated graphics?

---

### Post by kanikilu on 2012-05-25
> **ScrufffyJoe said:**
> The options for integrated graphics are "Auto" and "Force". Which one of these will actually disable the integrated graphics? I would assume "auto", but I use my integrated graphics on this computer...

To me, "force" implies that it's going to use the integrated graphics even if a discrete graphics card is installed.

---

