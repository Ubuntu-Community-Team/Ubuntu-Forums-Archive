---
title: "SAA7134 - Pulling Hair Out Now..."
date: 2006-03-24
forum: General Help
---

### Post by steele.campbell on 2006-03-24
Okay ladies and gents, I have something of a hair removing issue here and I am hoping you might be able to help me solve it.

I am trying to get a Mercury TV Tuner (Phillips saa7134) Card working in Ubuntu Breezy. I found a mention of it on the gentoo wiki and successfully modprobe'd the card with card=2 tuner=3 (I am NTSC, and from what I understand, 2 is PAL, NTSC is 3). I also added the module to /etc/modules for it. Now, here is the issue:

Initially, if I went into /dev/ I saw that I had a video0, vbio, and radio0, however nothing (kdetv, xawtv, mplayer) will find the card. The most verbose error I received was from tdetv where, after a few seconds it launches an error that says that it couldn't grab the video, and that I should play around with the v4l2 configuration. Now, however, radio0 is no longer displayed...

The relevant sections from:

*dmesg*
```
[4294699.620000] Linux video capture interface: v1.00
[4294699.641000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4294699.645000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[4294699.645000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKD] -> GSI 19 (level, high) -> IRQ 19
[4294699.645000] saa7130[0]: found at 0000:01:07.0, rev: 1, irq: 19, latency: 64, mmio: 0xfd400000
[4294699.645000] saa7130[0]: subsystem: 18d0:2100, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294699.645000] saa7130[0]: board init: gpio is 39100
[4294699.756000] saa7130[0]: i2c eeprom 00: d0 18 00 21 10 28 ff ff ff ff ff ff ff ff ff ff
[4294699.756000] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294699.756000] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294699.756000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294699.777000] saa7130[0]: registered device video0 [v4l2]
[4294699.778000] saa7130[0]: registered device vbi0
```

*lspci*
```
0000:01:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

```

ANyone have any hints, tips or next steps?

Much obliged and a beer will be owed to the individual who can solve this for me (it is the last thing I need configured before I wipe the WIndows partition).

---

### Post by steele.campbell on 2006-03-24
Bump

---

### Post by mp3guy on 2006-03-25
Try tvtime?

---

### Post by Jose Catre-Vandis on 2006-03-25
Just reread your dmesg listing. card=2 tuner=3 is not identifying the correct card/tuner (most probably card=2 is incorrect) even though gentoo wiki indicates otherwise

The trick will be in identifying the correct card and tuner,once you solve that puzzle, everything should start falling into place. Try only identifying the card as opposed to both card and tuner, e.g. 
```
sudo modprobe saa7134 card=4
```
remember to
```
sudo rmmod saa7134
```
each time you make a change

My card does not return the tuner I expected so a bit of trial and error might be necessary

I also suggest you install tvtime as this will help to check how things are working. Go to tvtime's pages to get help for setting things up, as depending on your graphics card setup you may need to make changes to settings there as well.

Best of luck, and keep checking dmesg and tvtime after each change.

---

### Post by pooler on 2006-03-25
Did you try using the card as root or the user you created durning installation? If it works, add your normal user to the group "video"

---

### Post by steele.campbell on 2006-03-26
Unfortunately, tvtime is not an option to me as I run an ATI x800XL with the fglrx drivers which apparently TVTIME doesn't support. It would seem my only options as far as software goes is a) aatv, b) XawTV (which just doesn't woulk), c)kdeTV.

I will try pooler's suggestion.

Thanks everyone and I'll keep you up-to-date.

---

### Post by Jose Catre-Vandis on 2006-03-26
[QUOTE=steele.campbell]Unfortunately, tvtime is not an option to me as I run an ATI x800XL with the fglrx drivers which apparently TVTIME doesn't support. It would seem my only options as far as software goes is a) aatv, b) XawTV (which just doesn't woulk), c)kdeTV.

I will try pooler's suggestion.

Thanks everyone and I'll keep you up-to-date.[/QUOTE]


I am running an ATi 9550, using fglrx drivers and tvtime works fine, maybe your newer card doesn't? You may need to adjust overlay settings (everyone else has had too :-)  ) Again check tvtime's pages, "Common problems" for what to do. You have to get your card recognised first though, you want to see it identified when you do a dmesg, rather than seeing

```
UNKNOWN/GENERIC [card=0,autodetected]
```
you should see your card make, e.g. Philips Saa7131 dual, hence the need for trial and error

---

