---
title: "How can I tell what video driver is being used?  How to change drivers?"
date: 2009-11-08
forum: General Help
---

### Post by akijikan on 2009-11-08
**MOBO:** Asrock 4CoreDual-SATA2
**CPU:** Pentium E5200 Dual-Core 2.5ghz
**RAM:** 1GB DDR-400
**Video:** ATI Radeon HD 2600XT 512MB **AGP** connected to 1080p montor via DVI.

I installed a wubi installation with a CRC checked 9.10 desktop ISO (AMD64).  However I experienced this problem with a LiveCD boot up too (verified the disc was good with check after burn and tried a couple other computers too).

Basically when I boot up my new installation I get a black screen with only a cursor.  If I move the cursor around it changes to the text-editing cursor over some areas, but all I see is black.

I can Alt+F* into the CLI.  If I go back to the xserver though it freezes and I have to hold down my power button.

I believe at this point it is something with my video.  My card is support by both the open and closed source ATI drivers, so I'm guessing that is what is loaded in my installation?  I'm not sure though.

So how can I tell what drivers are being used from the CLI.  If I wanted to try a more generic driver life flgrx, how could I go about that?

Thanks.

---

### Post by Tman5293 on 2009-11-08
Does your computer have integrated graphics as well? If so try connecting your monitor to that. If not try using VGA to install and then after install get your graphics card drivers to run off DVI. In this case I believe that your DVI connection is the problem so if you can use VGA either on the graphics card itself or with integrated graphics.

---

### Post by akijikan on 2009-11-08
No, I don't have any itegrated graphics, but I will give the VGA a try.  Now to find one of those dvi->vga adaptors I know is somewhere around here.

If it does turn out to be VGA, how would I go about getting the DVI to work once I completed the installation?

---

### Post by Tman5293 on 2009-11-08
The "Hardware Drivers Available" icon should pop up in the Notification Area after a few minutes then you just click it and install your video card drivers. After that DVI should work the next time you boot up.

---

### Post by akijikan on 2009-11-08
Well VGA didn't make a difference.  Still just a black screen with a cursor.

Is there a way I can change drivers with the CLI?

---

### Post by Mark Phelps on 2009-11-09
> **akijikan said:**
> Well VGA didn't make a difference.  Still just a black screen with a cursor.

Is there a way I can change drivers with the CLI?

See the link below for removing the ATI restricted drivers and replacing them with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

While your card is SUPPOSED to be supported under the latest ATI restricted drivers, I recall reading about problems specific to AGP versions of your card.  So, it may be that, in reality, only the PCI versions of your card are supported.

---

