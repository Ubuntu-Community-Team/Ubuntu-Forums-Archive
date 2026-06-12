---
title: "Projector dilemma"
date: 2010-06-15
forum: General Help
---

### Post by rodneysores on 2010-06-15
Hi, I'm trying to use my projector as a monitor with limited success.  In System>Display there are only two options; 800x600 and 640x480 both 4:3.  It seems as though the computer does not recognize the projector because when I move the computer to my TV many options show up.  Also, only on the projector, 'phantom squares' follow the mouse around and where windows have been closed.  Any ideas would be appreciated.  Thanks.

---

### Post by cbrunhaver on 2010-06-15
Are you connected directly from the video card to projector or are you going through some sort of switch or AV receiver?

It sounds like the EDID information isn't being passed correctly and that you may need to pull it out of the log and manually enter a modeline in your xorg.conf.

What video card and driver are you using?

---

### Post by rodneysores on 2010-06-15
I am connected directly to the projector and, you'll have to excuse my computer skill mediocrity, I'm not sure what sound card it is.  It's definitely whatever came in the computer which is a Compaq Evo ultraslim.  I have to leave for work soon but I'll try to find out what kind of card it is.  Thanks for the reply.

---

### Post by cbrunhaver on 2010-06-15
type this at the terminal and report back:

lspci | grep vga

---

### Post by rodneysores on 2010-06-16
I typed it in exactly as shown but nothing comes up.  Also, I had to move the computer to the TV again because I couldn't see the terminal window, only a white square.  I played around with the projector settings and colour settings on ubuntu with no change.

---

### Post by cbrunhaver on 2010-06-16
Well, just type "lspci" then look what it says for VGA.

By the way, the character I'm showing in that line is what you get with shift + backslash.  

I was just wondering what your video card is (your projector model would be helpful as well).

It seems that it is grabbing the EDID information correctly form the monitor but not the projector.

-Chris

---

### Post by rodneysores on 2010-06-16
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

The projector is Epson Powerlite Home 20

Thanks.

---

### Post by cbrunhaver on 2010-06-16
Okay, you have an intel 815 chipset (with integrated video) and a 480P projector, and so you want 720x480 resolution.

Unfortunately, I doesn't look like the i810/i815 supports widescreen resolutions.  I looked through a bunch of old threads on this (since this computer is about 10 years old now) and didn't find anything of use, though maybe there is a guru on here that can figure out if this can work.  I'm a relative n00b.

For my daughters old computer, I bought a PCI (not PCI-e) Geforce 8400gs a few moths ago for ~$30 and it breathed new life into that machine.

---

### Post by rodneysores on 2010-06-17
I guess I need a new video card, that sounds reasonable.  Thanks for all your help.

---

### Post by cbrunhaver on 2010-06-17
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187100&cm_re=8400GS_pci-_-14-187-100-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187100&cm_re=8400GS_pci-_-14-187-100-_-Product)

I would recommend something like this.  When using the nVidia proprietary driver, SMplayer or a bunch of other apps, you can use VDPAU in order to play back high def h.264 without very low CPU usage.

---

