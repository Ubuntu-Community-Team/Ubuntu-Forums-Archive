---
title: "Alsamixer Problem"
date: 2010-05-12
forum: General Help
---

### Post by sports fan Matt on 2010-05-12
I have seemed to encure a hissing sound from my speakers when I turn them on.  My alsa mixer settings:

What do i need to change?

---

### Post by sports fan Matt on 2010-05-13
I'm not 100 percent sure but I think it may be an alsamixer issue. Any ideas on what I could look into?

---

### Post by ranch hand on 2010-05-13
Make sure that your digital output switch is is unchecked (off).

That is all I can think of that causes noise.

If that is not it I would look at every input switch an make sure they are off until it quits then turn the rest back on if you need them.

---

### Post by sports fan Matt on 2010-05-13
Thanks for the suggestion but where would I check for this?

---

### Post by sports fan Matt on 2010-05-13
Here is my alsa config now:

No sound at all.

---

### Post by ranch hand on 2010-05-13
Well, that was fun.  I was in the middle of a reply and my 10.10 crashed.  Now where was I?

Ah, I would;
```

apt-get install gnome-alsamixer

```
I think it works a bit better but not sure why.  It has a very nice gui.

On the terminal alsa output you navigate with the arrow and tab key if I remember right.  Make sure that you get to every thing.  There is almost 2 screens left to right.

Not knowing what your sound card or controller is I can tell you that with my card (Audigy1) the gnome-alsamixer works better and the gui has every thing on it but you can get rid of what you will never want in preferences.

I have a workspace dedicated to it.  I can highlight the master volume and turn the monitor off and control the volume with the arrow keys, or work on other spaces and when I go back the thing is high lighted and ready to work with the arrrow keys.  Yes I know I can scroll the wheel on the sound applet but with the miser I can control so much more on my nice surround sound system.

---

### Post by sports fan Matt on 2010-05-13
Funny it is installed.  Lspci if you need it: 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
01:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)

---

### Post by sports fan Matt on 2010-05-13
Ive decided since Im wired awake I'll just spend an hour reinstalling lucid.  (Was gonna clean install at some point today anyway)

---

### Post by ranch hand on 2010-05-13
I don't blame you a bit.

I like clean installs.  They work better than upgrades and are sure better than left over testing installs that have been treated poorly for some time.

I even know how to grab my config files first so that I can compare them to the new ones.

My clean 10.04 installs boot faster and better than the left overs and a whole lot better than the upgraded ones from testing (I am still using the same one as my main though but the boot time sucks).

---

