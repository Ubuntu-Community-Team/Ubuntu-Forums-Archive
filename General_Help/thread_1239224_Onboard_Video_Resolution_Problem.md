---
title: "Onboard Video Resolution Problem"
date: 2009-08-13
forum: General Help
---

### Post by Malkosha on 2009-08-13
I'm installing 9.04 on a friends PC. Its an HP with onboard video using 32M of shared memory. Sadly, the onboard video is a S3 SavagePro.

After the install, the best resolution I can get is 800x600. Under Windows, I can easily get 1024x768 which is exactly want I want in 9.04.

I've tried everything from xrandr to altering the xorg.conf but the best that I can get is altering xorg to get 1024x768 in virtual mode. While virtual mode is sort of interesting since you can slide the screen around, its really kind of useless in this case.

I've restored the original xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
&#65279;
Since Windows was able to display this resolution, I know it can be obtained. Whether Ubuntu is able to do this however, remains to be seen. At the momnet, it looks rather bleak and I would hate to put Windows back on again.

So ... any help would be appreciated.

Thanks!

---

### Post by P4man on 2009-08-13
where you trying with the vesa or savage driver?
Try forcing the savage driver in xorg.conf.

edit: this may also help:
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

---

### Post by Malkosha on 2009-08-13
> **P4man said:**
> where you trying with the vesa or savage driver?
Try forcing the savage driver in xorg.conf.

edit: this may also help:
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)


I'm not really sure. When I ran the updates, I looked at synaptic to see what driver was installed and if there was an update. The Savage driver is installed but I'm not sure how to force xorg to use it nor do I know if it is using it or not. In the device section of xorg, I'm getting "configured video device" which seems rather genric to me. Research time!

Thanks for the info. I will search on how to do this.

---

### Post by jrader on 2009-08-13
> **P4man said:**
> where you trying with the vesa or savage driver?
Try forcing the savage driver in xorg.conf.

edit: this may also help:
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)
I also have a very similar problem. Resolution 800x600 and in windows much higher but 1024x768 would be OK for me. The xorg.conf is generic. I have no idea of make of my video card and I have a Sony CPD-e240 monitor. Rather try fix the problem i wouldlike  just buying a monitor and video card that would be automatically detected any suggestions. Would I need to re-install or would they  be detected on boot.

---

### Post by Bucky Ball on 2009-08-13
Don't they use the Unichrome drivers? My wife's machine is a Via chipset that has S3 and I think that is what I am using on there. Will check tomorrow what it is exactly.

Hold on, this might work! Go to Synaptic Package Manager, search for and install:

xserver-xorg-video-savage

Says it is specifically for your hardware. This may overwrite your xorg.conf file so if you have any custom tweaks in there best to remember what they are. Make a copy of the one you have now and then maybe meld the two together. Good luck. :)

---

### Post by P4man on 2009-08-13
xserver-xorg-video-savage is installed by default. Wouldnt hurt checking or reinstalling, but I doubt thats it

And unichrome drivers don't support the older S3 savage chips.

---

### Post by P4man on 2009-08-13
> **jrader said:**
> I also have a very similar problem. Resolution 800x600 and in windows much higher but 1024x768 would be OK for me. The xorg.conf is generic. I have no idea of make of my video card and I have a Sony CPD-e240 monitor. Rather try fix the problem i wouldlike  just buying a monitor and video card that would be automatically detected any suggestions. Would I need to re-install or would they  be detected on boot.

That seems a bit drastic. Lets find out what you have first, open a terminal and type:

```
lspci
```

post the result here.

---

### Post by jrader on 2009-08-13
> **P4man said:**
> That seems a bit drastic. Lets find out what you have first, open a terminal and type:

```
lspci
```

post the result here.
jack@jack-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)

---

### Post by jrader on 2009-08-13
> **jrader said:**
> jack@jack-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)
Data stamped on video card "ATI Rage XL 8MB PCI" "125MHZ Memory clock 8MB 1600x1200".

---

### Post by P4man on 2009-08-14
eww.. ouch heh.
you're gonna have a hard time buying a video card that works in that machine, at most thats an AGP 2x controller. Buying the wrong card (wrong voltage) can actually fry your machine.

I suggest you try these steps first:

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

And if you're gonna spend money, look on ebay for  a new machine all together.

---

### Post by jrader on 2009-08-14
> **P4man said:**
> eww.. ouch heh.
you're gonna have a hard time buying a video card that works in that machine, at most thats an AGP 2x controller. Buying the wrong card (wrong voltage) can actually fry your machine.

I suggest you try these steps first:

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

And if you're gonna spend money, look on ebay for  a new machine all together.
Thank you. This was just something I built from old parts laying around. I would to build a another just for Linux use. I don't do games but internet browsing news, blogs, letters to editor, political comments. Could suggest a mother board, and interface cards that would work best?

Except for the video resolution this old machine works pretty could. I have two others that I use one primarily for XP home office and Video processing on the other.

Thank you for your help.

---

### Post by P4man on 2009-08-14
new motherboard means new cpu, means new ram. probably even means new psu.

its your money, but id try that link first :) The card should be able to handle higher resolutions.

---

### Post by jrader on 2009-08-14
Thanks for help. I'll give it try.

---

### Post by Bucky Ball on 2009-08-15
If you do build a new computer (although if you can use any of your exisiting bits do and the rest give away, sell or recycle wisely) you might like to check out the link in my signature. :)

---

