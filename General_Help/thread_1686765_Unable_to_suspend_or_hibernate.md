---
title: "Unable to suspend or hibernate"
date: 2011-02-12
forum: General Help
---

### Post by flylehe on 2011-02-12
My Ubuntu 10.10 on my laptop Lenovo T400 is not able to suspend or hibernate.

[LIST=1]
[*]Whenever I click Suspend or Hibernate in Startup options of the OS:
    * the moon LED on the bottom of the lid flashes a few seconds, the screen quickly shows something like "some devices fail to suspend, error 5",
    * and then the moon LED goes off and the display still has ambient light illumination. I suppose in suspend or hibernation state, the display should have no illumination, just like when the laptop is turned off, right?
    * If I press any key, the unlock screen dialogue will pop out.

[*]I have installed 'acpi-support' and 'hibernate 1.99-1.1'. But I don't know how to use these methods to suspend or hibernate my OS. Are they by commands in terminate, or can they be called by clicking Suspend or Hibernate in Startup options of the OS? For example, I type the hibernation command and it shows something is missing although I have installed "tuxonice-userui" ( I don't know if it will provide Tuxonice binary signature file):
```

$ sudo hibernate
hibernate:Warning: Tuxonice binary signature file not found.

```

[*]I also found that Kernel 2.6.35 cannot suspend nor hibernate; Kernel 2.6.32 can suspend but cannot hibernate (it shows a screen of successfully writing the content of RAM to file when clicking Hibernate, but when I try to wake it up by pressing startup key on the keyboard, it restarts instead of waking up).
[/LIST]

Any suggestions to solve this problem? Thanks and regards!

**********************************************************************

PS:

My Laptop specifications:
> 
CPU
    Intel Mobile Core 2 Duo P8800  @ 2.66GHz
    Penryn 45nm Technology
RAM
    1.9GB Single-Channel DDR3 @ 532MHz (7-7-7-20)
Motherboard
    LENOVO 2764CTO (None)
Graphics
    ThinkPad Display 1440x900 @ 1440x900
    ATI Mobility Radeon HD 3400 Series (Lenovo)
Hard Drives
    244GB Western Digital WDC WD2500BEVS-08VAT2 (SATA)
Optical Drives
    HL-DT-ST DVDRAM GSA-U20N
    AZCDW EFCPUZ452 SCSI CdRom Device
    AZCDW EFCPUZ452 SCSI CdRom Device
Audio
    Conexant 20561 SmartAudio HD

Swap for Ubuntu is 4 GB.

---

### Post by apastuszak on 2011-02-13
Having the same issue.  The laptop actually suspends without error, but immediately wakes up.  When I look at the pm-suspend log, everything seems to shut down fine, and them 2 seconds later it just says AWAKE in the log, like I initiated a wakeup.  I went into the BIOS and turned on discreet graphics and turned off OS detection of graphics card, because I wanted to use the ATI graphics.

I'll try and switch to Intel and see if that makes a difference.  I read on another thread that 2.6.36 fixes the issue, but if I install that, I'll break the ATI driver, since I am sure it's compiled against 2.6.35.  Sigh...

---

### Post by apastuszak on 2011-02-18
I fixed it!  There was a very nice writeup on the Gentoo Linux wiki on the T400.

[http://en.gentoo-wiki.com/wiki/Lenovo_ThinkPad_T400](http://en.gentoo-wiki.com/wiki/Lenovo_ThinkPad_T400)

Here is what I did:

I went into /etc/modprobe.d and created a file called tpm-workaround.conf and put the following lines in it:

#without this, my t400 would not suspend
options tpm_tis itpm=1

I then rebooted and suspend worked great.  Great writeup from the Gentoo guys on the T400.

---

