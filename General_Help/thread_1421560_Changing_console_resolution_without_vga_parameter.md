---
title: "Changing console resolution without vga parameter"
date: 2010-03-04
forum: General Help
---

### Post by Chikitulfo on 2010-03-04
Hello everybody!
Didn't know where to put this so I decided to post in general help.

Let's start with some context: About a week ago, I saw in the university computer that the text mode consoles(ctrl+alt+f[n]) worked with a great resolution on a 19" wide screen (I think it is 1440x900) running fedora 11. So I wondered if I could make the text consoles at home to work with a good resolution also.

So I started to search for that and found the kernel parameter vga= . The problem: it doesn't support 1440x900 or any other 16:10 resolution for my graphic card. Then I thought that maybe fedora uses some module that allows that, because the livecd allows a good resolution (by default) on my desktop computer.

What I thought so far is that fedora is not using vesa for the virtual console (which i think is the driver that ubuntu uses) and I want to know what driver it is and how to use it in ubuntu (either compiling the kernel or simply installing something).

I don't even know if my guesses are right or not. But I've gathered some info so far:

From /var/log/messages (fedora 12 livecd) I got this part, which I think is the really interesting one.
> Mar  2 22:37:18 localhost kernel: [drm] Initialized drm 1.1.0 20060810
Mar  2 22:37:18 localhost kernel: [drm] radeon defaulting to kernel modesetting.
Mar  2 22:37:18 localhost kernel: [drm] radeon kernel modesetting enabled.
Mar  2 22:37:18 localhost kernel: radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  2 22:37:18 localhost kernel: [drm] radeon: Initializing kernel modesetting.
Mar  2 22:37:18 localhost kernel: [drm] register mmio base: 0xFE8E0000
Mar  2 22:37:18 localhost kernel: [drm] register mmio size: 65536
Mar  2 22:37:18 localhost kernel: ATOM BIOS: Wekiva
Mar  2 22:37:18 localhost kernel: [drm] Clocks initialized !
Mar  2 22:37:18 localhost kernel: [drm] Detected VRAM RAM=256M, BAR=256M
Mar  2 22:37:18 localhost kernel: [drm] RAM width 256bits DDR
Mar  2 22:37:18 localhost kernel: [TTM] Zone  kernel: Available graphics memory: 2029280 kiB.
Mar  2 22:37:18 localhost kernel: [drm] radeon: 256M of VRAM memory ready
Mar  2 22:37:18 localhost kernel: [drm] radeon: 512M of GTT memory ready.
Mar  2 22:37:18 localhost kernel: [drm] Loading RV770 CP Microcode
Mar  2 22:37:18 localhost kernel: platform radeon_cp.0: firmware: requesting radeon/RV770_pfp.bin
Mar  2 22:37:18 localhost kernel: platform radeon_cp.0: firmware: requesting radeon/RV770_me.bin
Mar  2 22:37:18 localhost kernel: [drm] GART: num cpu pages 131072, num gpu pages 131072
Mar  2 22:37:18 localhost kernel: usb 6-2: new full speed USB device using uhci_hcd and address 2
Mar  2 22:37:18 localhost kernel: [drm] ring test succeeded in 1 usecs
Mar  2 22:37:18 localhost kernel: [drm] radeon: ib pool ready.
Mar  2 22:37:18 localhost kernel: [drm] ib test succeeded in 0 usecs
Mar  2 22:37:18 localhost kernel: [drm] Radeon Display Connectors
Mar  2 22:37:18 localhost kernel: [drm] Connector 0:
Mar  2 22:37:18 localhost kernel: [drm]   DVI-I
Mar  2 22:37:18 localhost kernel: [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
Mar  2 22:37:18 localhost kernel: [drm]   Encoders:
Mar  2 22:37:18 localhost kernel: [drm]     DFP1: INTERNAL_UNIPHY
Mar  2 22:37:18 localhost kernel: [drm]     CRT2: INTERNAL_KLDSCP_DAC2
Mar  2 22:37:18 localhost kernel: [drm] Connector 1:
Mar  2 22:37:18 localhost kernel: [drm]   DIN
Mar  2 22:37:18 localhost kernel: [drm]   Encoders:
Mar  2 22:37:18 localhost kernel: [drm]     TV1: INTERNAL_KLDSCP_DAC2
Mar  2 22:37:18 localhost kernel: [drm] Connector 2:
Mar  2 22:37:18 localhost kernel: [drm]   DVI-I
Mar  2 22:37:18 localhost kernel: [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
Mar  2 22:37:18 localhost kernel: [drm]   Encoders:
Mar  2 22:37:18 localhost kernel: [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Mar  2 22:37:18 localhost kernel: [drm]     DFP2: INTERNAL_KLDSCP_LVTMA
Mar  2 22:37:18 localhost kernel: [drm] fb mappable at 0xD0141000
Mar  2 22:37:18 localhost kernel: [drm] vram apper at 0xD0000000
Mar  2 22:37:18 localhost kernel: [drm] size 5299200
Mar  2 22:37:18 localhost kernel: [drm] fb depth is 24
Mar  2 22:37:18 localhost kernel: [drm]    pitch is 5888
Mar  2 22:37:18 localhost kernel: executing set pll
Mar  2 22:37:18 localhost kernel: executing set crtc timing
Mar  2 22:37:18 localhost kernel: [drm] TMDS-9: set mode 1440x900 1d
Mar  2 22:37:18 localhost kernel: Console: switching to colour frame buffer device 180x56
Mar  2 22:37:18 localhost kernel: fb0: radeondrmfb frame buffer device
Mar  2 22:37:18 localhost kernel: registered panic notifier
Mar  2 22:37:18 localhost kernel: [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0

And that is all I have so far.

If anybody could help me with any of this I'd appreciate it; because my knowledge of the true insides of linux is none and I really want a good resolution under text mode (without having to switch to fedora ;) )

PS: My machine: Intel quad q6600, Ati Radeon HD4850; Ubuntu 9.10; TFT LG 19" Widescreen (1440x900, 16:10).

---

### Post by Chikitulfo on 2010-03-06
Hi again,
I found that while fedora uses radeon (or that is what i think from the messages above) ubuntu is using vesafb:
```
$ dmesg | grep fb
[    0.651104] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe7f8000-0xfe7fbfff]
[    0.651546] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe7ff800-0xfe7ffbff]
[    2.507490] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011200000, using 320k, total 320k
[    2.507493] vesafb: mode is 640x480x8, linelength=640, pages=0
[    2.507495] vesafb: scrolling: redraw
[    2.507497] vesafb: Pseudocolor: size=0:8:8:8, shift=0:0:0:0
[    2.507533] fb0: VESA VGA frame buffer device
[   16.554830] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 

```

So I think that I only need to change the vesafb module for radeonfb.

Any clue on how to use radeon instead of vesa?

BTW this seems to interest very little out there :D

[COLOR="DarkOrange"]**EDIT: FINALLY!!**[/COLOR] 
I found that what i was looking for is KMS (Kernel Mode Setting), a rather new feature included in fedroa since Fedora 11 hat ubuntu doesn't use. 
This allows the use of advanced graphics in the kernel, so the VTs look really good.
I'll see if i can make it work on ubuntu.

---

### Post by dcstar on 2010-12-31
> **riptone said:**
> Glad to follow what you said, I've been looking for the answer for long time.

Huh?, altering the Grub2 default file allows setting the resolution of these terminals to any VESA mode and these answers have been around for a long time.

---

