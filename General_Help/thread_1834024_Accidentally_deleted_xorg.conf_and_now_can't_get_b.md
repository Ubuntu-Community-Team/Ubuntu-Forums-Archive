---
title: "Accidentally deleted xorg.conf and now can't get back to 1680x1050 res"
date: 2011-08-26
forum: General Help
---

### Post by .mouse on 2011-08-26
I was getting swamped in terminals and accidentally used rm when I meant to use gedit.  I'm trying to remake xorg.conf and can't get the resolution back to 1680x1050.  In nvidia-settings the max available resolution is 1360x768 but before deleting xorg.conf it had several different higher settings including 1680x1050.

So far I've tried nvidia-xconfig, tried to force the change with xrandr, tried "sudo /etc/init.d/gdm stop && sudo X -configure && sudo cp xorg.conf.new  /etc/X11/xorg.conf && /etc/init.d/gdm start", tried "sudo dpkg-reconfigure xserver-xorg", tried "sudo Xorg -configure", tried changing xorg-config manually, even uninstalling and reinstalling the nvidia drivers and a few other things I can't remember and nothing can increase the resolution beyond 1360x768.

xorg-conf:
[http://pastebin.com/db6Skb9y](http://pastebin.com/db6Skb9y)

Ubuntu 64bit 10.04
nvidia geforce 9600 GT

If anyone can help get me out of this mess I would GREATLY appreciate it.

Thanks in advance.

EDIT
I went digging around in xorg.0.log here:
[http://pastebin.com/fncR80Tu](http://pastebin.com/fncR80Tu)
and found a couple lines that stuck out:
```
 (WW) Aug 27 13:13:36 NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
(WW) Aug 27 13:13:36 NVIDIA(GPU-0):     unrecognized EDID Header.

```So after doing "sudo get-edid | parse-edid" I got:
```
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "NVIDIA"

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
    Call failed

The EDID data should not be trusted as the VBE call failed
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).

    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:50 3:ff
    Identifier "TG_:0000"
    VendorName "TG_"
    ModelName "TG_:0000"
    # Block type: 2:50 3:ff
    # DPMS capabilities: Active off:no  Suspend:yes  Standby:no

    Mode     "1616x3866"    # vfreq 7.882Hz, hfreq 61.372kHz
        DotClock    146.250000
        HTimings    1616 1728 1784 2383
        VTimings    3866 3919 3967 7786
        Flags    "+HSync" "-VSync"
    EndMode
    Mode     "1280x511"    # vfreq 102.219Hz, hfreq 426.354kHz
        DotClock    653.600000
        HTimings    1280 1360 1615 1533
        VTimings    511 543 575 4171
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    # Block type: 2:50 3:ff
    Mode     "1280x1023"    # vfreq 397.571Hz, hfreq 425.798kHz
        DotClock    653.600000
        HTimings    1280 1360 1615 1535
        VTimings    1023 1058 1090 1071
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
EndSection
```
I think this is EDID related but the EDID can't be corrupt because it was working just fine before xorg.conf got deleted.  I was going to use customedid but I can't find any edid.bin on my system.  I've never done this before.  Does anyone have any experience with this?

---

### Post by .mouse on 2011-08-27
Success!

Every site I ran across said you can create an edid.bin file through nvidia-settings but there is no feature for that in my nvidia-settings even running at terminal level.  So....

Modifying the instructions at:
[http://analogbit.com/fix_nvidia_edid](http://analogbit.com/fix_nvidia_edid)

I downloaded Phoenix EDID Designer, booted into win7 and imported my EDID(the instructions said to set the extensions field to 0 but it was already 0).  Then I exported it to a .raw file and rebooted back into Ubuntu and moved the file to /etc/X11/edid.raw and added this line to /etc/X11/xorg.conf:
```
    Option "CustomEDID" "CRT-0:/etc/X11/edid.raw"
```Then just save and reboot system/restart X and success!

Screen res is at 1680x1050@60hz and it has never looked better!

Additionally now that I'm using a custom EDID the "Acquire EDID..." button is now available in nvidia-settings

Strange though... looks like wind'ohs saved the day....  Guess it couldn't stay useless forever.  =P  I kid of course.  I hope this will help anyone with a similar problem in the future.

---

### Post by ninjaaron on 2011-08-27
> **.mouse said:**
> I was getting swamped in terminals and accidentally used rm when I meant to use gedit.

:shock:

epic.


Since you solved the problem (and a fine job, I might add), you ought to mark the thread as "sloved" using the thread tools at the top of the page.

---

