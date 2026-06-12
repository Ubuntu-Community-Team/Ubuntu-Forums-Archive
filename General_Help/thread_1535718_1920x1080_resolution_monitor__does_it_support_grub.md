---
title: "1920x1080 resolution monitor : does it support grub?"
date: 2010-07-21
forum: General Help
---

### Post by banskt on 2010-07-21
I installed Ubuntu 10.04 on a new system. 

The system is not showing correct resolution in the grub menu and the splash screen is black, until I reach the logon screen.

Screen resolution, and video rendering after booting is picture-perfect.

**My system:**
Ubuntu 10.04 Lucid Lynx | 2.6.32-23-generic
AMD Phenom II X6 1055T
Gigabyte GA-MA785GMT-US2H 
        Onboard Graphics: ATI Radeon HD4200
Dell U2211H monitor (1920x1080@60Hz)

**Other info:**
root#  lsmod|grep fglrx
```
fglrx                2353422  32 
```root# xresprobe fglrx
```
id: DELL U2211H
res: 1920x1200 1920x1080 1280x1024 1152x864 1024x768 800x600 720x400 640x480
freq: 30-83 56-76
disptype: 

```root# get-edid | parse-edid
```
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0xc01cc "ATI ATOMBIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

parse-edid: EDID checksum passed.

    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fc
    Identifier "DELL U2211H"
    VendorName "DEL"
    ModelName "DELL U2211H"
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:fd
    HorizSync 30-83
    VertRefresh 56-76
    # Max dot clock (video bandwidth) 170 MHz
    # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

    Mode     "1920x1080"    # vfreq 60.000Hz, hfreq 67.500kHz
        DotClock    148.500000
        HTimings    1920 2008 2052 2200
        VTimings    1080 1084 1089 1125
        Flags    "+HSync" "+VSync"
    EndMode
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:fd
EndSection
```

root# hwinfo --framebuffer
```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.NSbTZunW9ID
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  RS880"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "RS880"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 24 bits
  Mode 0x0383: 1792x1344 (+1792), 8 bits
  Mode 0x0385: 1792x1344 (+3584), 16 bits
  Mode 0x0386: 1792x1344 (+7168), 24 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 24 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

vbeinfo at grub command gives the same output.


**What I have done till now?**

a. tried changing **GRUB_GFXMODE=1920x1080** in */etc/default/grub* -- doesn't work.
black screen - error message is "The current input timing is not supported by the monitor display"

b. added another line **GRUB_GFXPAYLOAD_LINUX=keep** in */etc/default/grub* -- doesn't work.
same error message.
```

To see the /etc/default/grub file after the above changes: 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1080
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

c. installed **uvesafb** and **v86d**, and made the grub work in 1280x1024 -- though still no support for 1920x1080.

I presume this is a bug of the sort "VBE does not support 1920x1080 wide screen resolution".
Or, maybe I am missing some point.
I hope there must be some workaround.

---

### Post by RTrev on 2010-07-21
I can't give you specific advise, beyond saying that it seems that the boot process has been a complete mess ever since Edsel (excuse me, I mean "Plymouth") was introduced.  As long as you can login, and get the right resolution, you're doing well.  I think there are some grub options about the resolution to use, but while they may help with the actual grub menu itself I don't think they're going to make any difference once the boot process begins.

I've been known to be wrong, however. ;)

---

### Post by banskt on 2010-07-23
The "Plymouth Problem" is still unsolved. 

I was having some problem configuring 3D acceleration on my desktop using ATI Catalyst driver. Thanks to kronictokr, I replaced the video drivers -- [see here]("http://ubuntuforums.org/showthread.php?p=9180103#post9180103")...

But still, the problem persists, and I am seeing huge fonts at the grub menu...

---

### Post by kronictokr on 2010-07-23
try my method without the added option at the end, my fonts change as it says loading bottom script..... in grub, as long as you have KVM installed, and you should if you followed my tut

if its perfect after booting, i would be happy, this is ubuntu , so unless you are obsesive compulsive like myself, finding a solution may be more tedious than you may care for.

oh, and i also, have been know to be wrong, from time to time :P

---

### Post by banskt on 2010-07-24
Yes, for me also, the fonts change after loading init-bottom scripts...

The problem is before that... as I mentioned in my first post, after the booting is complete, everything is perfect... no problem there...

And, I fear that grub do not have access to xorg.conf file, so it should not be anything related to xorg.conf.
Yet, I tried specifying the screen resolution in xorg.conf, but that is not solving the problem. 

I understand that I can live with it, but as I am a bit meticulous about things, finding a solution might not be a bad idea. 

Still playing around with whatever little knowledge I have, but definitely I need your help....

---

### Post by dcstar on 2010-07-24
> **banskt said:**
> 
.........
I understand that I can live with it, but as I am a bit meticulous about things, finding a solution might not be a bad idea. 

Still playing around with whatever little knowledge I have, but definitely I need your help....

Grub - or any boot loader - can **only** use the basic VESA resolutions that are available, they have little to do with the advanced resolutions available in full graphics mode.

There are many things already on the net explaining this.

---

### Post by banskt on 2010-07-24
> **dcstar said:**
> Grub - or any boot loader - can **only** use the basic VESA resolutions that are available, they have little to do with the advanced resolutions available in full graphics mode.

Now that's where the main question comes in - VESA is not recognising the 1920x1080 resolution - is there any feasible method by which I can help it to recognise?

Please refer to my first post, where I have mentioned the details.


> **dcstar said:**
> 
There are many things already on the net explaining this.

Yes, I have googled and tried a lot of methods, but still....

---

### Post by QIII on 2010-07-24
We know that the plymouth issue exists.  It will undoubtedly be resolved.  

My question is this:

Why on earth are we making such a fuss over something we see for 5 - 7 seconds out of the several hours we may be using our machines?

It seems a silly thing to get our bowels in an uproar over.

---

### Post by kronictokr on 2010-07-25
in all id have to agree, for 5-7 seconds, the rest tic's and toc's just fine. slams windows7

---

### Post by dcstar on 2010-07-25
> **banskt said:**
> Now that's where the main question comes in - VESA is not recognising the 1920x1080 resolution - is there any feasible method by which I can help it to recognise?

Please refer to my first post, where I have mentioned the details.

Yes, I have googled and tried a lot of methods, but still....

The VESA standard **does not** support those resolutions - be told.

---

### Post by prodigy_ on 2010-07-25
Try [this workaround](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml). 1920x1080 won't work (because VBE doesn't support it at all), but 1280x1024 will.

---

### Post by banskt on 2010-07-25
> **QIII said:**
> We know that the plymouth issue exists.  It will undoubtedly be resolved.  
> **dcstar said:**
> The VESA standard **does not** support those resolutions - be told.
> **prodigy_ said:**
> 1920x1080 won't work (because VBE doesn't support it at all)

I 'm confused :confused:

> **QIII said:**
> Why on earth are we making such a fuss over something we see for 5 - 7  seconds out of the several hours we may be using our machines?
"Because it's there."
As I mentioned before, there are many more important problems than this one.. but still, it's a problem. Maybe it's sounding rather silly ... but still, why should there be a problem? As compared to its windows counterpart, everything goes normal after the grub screen... the boot splash takes place at 1920x1080... hence I am pretty sure, Ubuntu can also do that... so why not try it out?

> **prodigy_ said:**
> Try [this workaround]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml"). 
Thanks...
But, I have already tried that method...
Please note in my original post, I have mentioned ...
> **banskt said:**
> 
*snip*

[B]What I have done till now?

[/B]//......

c. installed **uvesafb** and **v86d**, and made the grub work in 1280x1024 -- though still no support for 1920x1080.


---

### Post by dcstar on 2010-07-25
> **banskt said:**
> I 'm confused :confused:

"Because it's there."
As I mentioned before, there are many more important problems than this one.. but still, it's a problem. Maybe it's sounding rather silly ... but still, why should there be a problem? As compared to its windows counterpart, everything goes normal after the grub screen... the boot splash takes place at 1920x1080... hence I am pretty sure, Ubuntu can also do that... so why not try it out?


Yes, confused is correct - you do not just understand what is happening.

Grub - and the following Plymouth splash screen - only use the VESA resolutions built into the video cards.

The Windows "equivalent" of Grub is a standard text screen that you get when you press F8, and that does not do widescreen resolutions either.

Only after the initial booting phase is completed then the full OS takes over, activates all the non-VESA functions of the video card and provides the login screen that you see.

---

### Post by banskt on 2010-07-25
> **dcstar said:**
> 
Grub - and the following Plymouth splash screen - only use the VESA resolutions built into the video cards.


Yes, I understand that.... and that's where I need your help. I want to have VESA recognise the widescreen resolution.

Is it possible?

I must re-iterate here that i have also not been able to do it with uvesa....

Any solution, be it uvesa or vesa, will do.

---

### Post by prodigy_ on 2010-07-25
> **banskt said:**
> Is it possible?

Okay. If you want, try this little script but I can't guarantee that it'll work: ```


#!/bin/sh

apt-get install v86d

VBE_FBR="1920x1080"

sed -i -e 's/\(GRUB_CMDLINE_LINUX_DEFAULT=\).*/\1"quiet splash nomodeset video=uvesafb:mode_option='${VBE_FBR}'-32,mtrr=3,scroll=ywrap"/' /etc/default/grub
sed -i -e 's/.*\(GRUB_GFXMODE=\).*/\1'${VBE_FBR}'x32/' /etc/default/grub
touch /etc/initramfs-tools/modules
if	[ -z "$(grep 'uvesafb ' /etc/initramfs-tools/modules)" ]
then
	printf "%s\n" "uvesafb mode_option=${VBE_FBR}-32 mtrr=3 scroll=ywrap" >> /etc/initramfs-tools/modules
else
	sed -i -e 's/.*\(uvesafb \).*/\1mode_option='${VBE_FBR}'-32 mtrr=3 scroll=ywrap/' /etc/initramfs-tools/modules
fi
touch /etc/initramfs-tools/conf.d/splash
if	[ -z "$(grep 'FRAMEBUFFER=' /etc/initramfs-tools/conf.d/splash)" ]
then
	printf "%s\n" "FRAMEBUFFER=y" >> /etc/initramfs-tools/conf.d/splash
else
	sed -i -e 's/.*\(FRAMEBUFFER=\).*/\1=y/' /etc/initramfs-tools/conf.d/splash
fi
update-grub
update-initramfs -u
```

Save this script in your Home Folder as a text file called, for example, **grub-vbe.sh** and then run it as root: ```
sudo sh ~/grub-vbe.sh
```

---

### Post by QIII on 2010-07-25
> **banskt said:**
> "Because it's there."

Yes.  It is.  It is well documented.  Everyone knows it exists.  I am quite certain it is being worked on.

Bringing is up again and again will not suddenly make someone say "Oh, dear!  We haven't been trying to resolve this despite the fact that everyone has been complaining about it!  We should, at long last, begin to work on this!  We've upset banskt <insert any other user here -- I'm not picking on you>!"

There are many, many more problems that present much more significant usability issues than this one.

---

### Post by banskt on 2010-07-26
> **prodigy_ said:**
> Okay. If you want, try this little script but I can't guarantee that it'll work: 
*snip*


Thanks...

Tried that, didn't work, changed back everything to the way they were before running the script.. 
It might be mentioned here that this script does the same thing as [discussed here]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml").. 

> **QIII said:**
> 
There are many, many more problems that present much more significant  usability issues than this one.

Well, so for the time being I think I should give up this issue, settling for a 1280x1024 resolution (only grub menu and splash screen.... ) on a otherwise widescreen (1920x1080) monitor... (note here that the video rendering / resolution after bootup is perfect.)

However if somebody is interested to solve this problem, or wants to suggest me something, he is always welcome. I am keeping this thread open. 

Thanks to all of you for your valuable time and opinions.

---

### Post by prodigy_ on 2010-07-26
> **banskt said:**
> Tried that, didn't work...
Then probably right now nothing will work, short of writing your own video driver.

---

### Post by P1C0 on 2010-12-11
You need to run:
pico@oblivion:~$ sudo hwinfo --framebuffer
and find out what is supported.

For example I also have a 1920x1080 monitor, but only following resolutions are supported:
pico@oblivion:~$ sudo hwinfo --framebuffer
[sudo] password for pico: 
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: 
  Hardware Class: framebuffer
  Model: 
  Vendor: "NVIDIA Corporation"
  Device: 
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xcf000000-0xcfdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

So I picked the 1280x800 which comes closer to 16:9 and maintains a high resolution. Unless there is a 1920x1080 entry I don't think it is possible to have that kind of resolution for plymouth splash screen.

Just pick a 24-bit entry, if possible in 16:9 resolution (1280x720 etc).

---

### Post by ontwowheels on 2011-05-16
Are you still having a problem with this?  I was on a new install 64bit NN install.  This link fixed it for me, I just changed the resolutions stated to 1920x1080.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

---

### Post by whalogreg on 2011-07-16
> **QIII said:**
> Yes.  It is.  It is well documented.  Everyone knows it exists.  I am quite certain it is being worked on.

Bringing is up again and again will not suddenly make someone say "Oh, dear!  We haven't been trying to resolve this despite the fact that everyone has been complaining about it!  We should, at long last, begin to work on this!  We've upset banskt <insert any other user here -- I'm not picking on you>!"

There are many, many more problems that present much more significant usability issues than this one.

That is why we have these forums. There are people out there that might not be committed to working on usability issues, but might be able, and even eager, to help with these problems. I really don't believe that the people working on usability bugs are taking time out of that, to look at these issues. I think it's wonderful that we can ask the community, and not just the devs for help. This thread is not a problem at all, in fact, just maybe some people in the community may collaborate and find work-arounds and fixes for some of these problems. 

I don't think that somebody that has their system running fine, except for their boot process, should just sit back and shut up because there are bigger fish to fry, because for them, there might not be. 

If you don't like it, don't waste your own time to read through posts like this, and simply offer up criticism instead of a welcoming, thoughtful (and maybe eventually) useful response. 

Posts like that drive people away from coming to forums like this, and make it seem like using linux based systems will just get them yelled at if there's something they'd like advice on.

P.S. Yes, I realize this issue has been brought up, but every system is different, and if you really look at it, they read up on it already, and fixes for other people hadn't worked for them. That is why they brought it up, with plenty of info, to see if they were missing something.

---

### Post by someids on 2012-09-09
this WORKS for me:

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

and I don't miss the biutiful screen

---

