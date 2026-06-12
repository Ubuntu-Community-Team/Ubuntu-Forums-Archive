---
title: "URGENT! THE IGNORED BUG: Connect-Debounce Failed"
date: 2010-02-26
forum: General Help
---

### Post by SaikoRonin on 2010-02-26
I have been getting a bug that has stumped me and countless others,  It is ignored when it is posted, and the bug is listed as not going to be fixed.

The linux bug report: [https://bugs.launchpad.net/linux/+bug/88530]("https://bugs.launchpad.net/linux/+bug/88530")

The Ubuntu bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/88530]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/88530")

This is the error I get over and over again upon startup and repeating in my system log indefinitely.

> Feb 26 10:48:14 ronin-desktop kernel: [118733.712028] hub 1-0:1.0: connect-debounce failed, port 7 disabled
Feb 26 10:48:16 ronin-desktop kernel: [118735.668020] hub 1-0:1.0: connect-debounce failed, port 7 disabled
Feb 26 10:48:18 ronin-desktop kernel: [118737.592019] hub 1-0:1.0: connect-debounce failed, port 7 disabled
Feb 26 10:48:20 ronin-desktop kernel: [118739.516020] hub 1-0:1.0: connect-debounce failed, port 7 disabled


The results of lsusb in terminal:
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


The results of lspci in terminal:
> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:01.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem
06:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
06:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

My mouse occasionally got laggy and stopped moving for a few seconds at a time for a month before this happened,  I looked for a way to fix it but couldnt so just ignored it.

Recently after upgrading to lucid lynx ( I believe this to be unrelated, see below) my usb mouse failed ubruptly... A cold reboot fixed it temporarily, but failed to fix it subsequently...  
I attempted to fix it in many ways but nothing worked.  And shortly after all usb devices failed to be detected(printer, thumb drive, mp3 player) However the mouse still shows the red laser when plugged in.

I then downgraded to Jaunty Jackalope from a CD I had.  The problem still existed so I checked my bios and it was up to date,  I set my gub menu to read "# defoptions=quiet splash acpi=force irqpoll" and still nothing.  I reinstalled my xorg.conf file,  and I made sure my usb ports were enabled in the Bios menu.


So what could be the problem?  I don't want to go back to windows,  and hopefully it isnt a hardware problem because I don't have the money for a new computer.

Maybe we can get this bug fixed once and for all...


Here are some forum links to the very same (or very similar) problem:

[Cbhargava]("http://ubuntuforums.org/showthread.php?t=156166")
[Jasonmichel]("http://ubuntuforums.org/showthread.php?t=1108034")
[Ajlewis2]("http://ubuntuforums.org/showthread.php?t=621362")
[CoachMark]("http://ohioloco.ubuntuforums.org/showthread.php?p=8876319")
[Xerxesv5]("http://ubuntuforums.org/showthread.php?t=231740")
[Lewench]("http://art.ubuntuforums.org/showthread.php?t=1115160")
[Balagosa]("http://www.backports.ubuntuforums.org/showthread.php?p=5673108")
[Elim]("http://swiss.ubuntuforums.org/showthread.php?t=57807")

---

### Post by clhsharky on 2010-02-26
Hi

Looks like a  Intel bug. Ubuntu cant fix that.
Have you reported the bug to Intel?

Sharky

---

### Post by SaikoRonin on 2010-02-26
No, I havent.  However can you be more specific when you say intel bug?  

I stuck an updated linux microcode .dat file in my firmware when i was trying to find solutions.  I'm not sure if it is being registered or would even solve the problem if it was working,

Im not a computer expert but Im learning what I can about Ubuntu and computers.

Are you saying it is a problem with my processors?

---

### Post by hwttdz on 2010-02-26
Have you tried another mouse in a different usb port?

---

### Post by SaikoRonin on 2010-02-26
All Usb Devices are not being read... it is not a problem with the mouse...

I located this driver on the intel website.  Will this help? and it is linux but it doesnt state if it is for debian systems or not.


[IXP400- USB Client Driver]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13754&ProdId=2100&lang=eng")

---

### Post by SaikoRonin on 2010-02-26
I don't think it is compatible,  and anyways it doesnt explain why it worked for a year before it failed,  maybe its a problem with the 2.6 kernel?

---

### Post by SaikoRonin on 2010-02-27
Does anyone know the cause of this issue?  Id like to have a definitive answer so that we can close the bug reports, and help all the people on the forum that have never had their questions answered.

---

### Post by SaikoRonin on 2010-02-28
bump

---

### Post by hwttdz on 2010-02-28
This is a support forum, not a developer forum.  I think there is a link to the bug report here.  That's the proper place to pursue a solution.

Nope, there wasn't a link to the bug report, please see here: [https://bugs.launchpad.net/linux/+bug/88530](https://bugs.launchpad.net/linux/+bug/88530)

Re-edit: actually it was in your original post.  Also are you running the most current kernel?  as this seems to be a kernel issue.

---

### Post by SaikoRonin on 2010-02-28
I was using 2.6.31 but after I downgraded my current information is

> Linux ronin-desktop 2.6.28-18-generic #59-Ubuntu SMP Thu Jan 28 01:23:03 UTC 2010 i686 GNU/Linux

Can someone explain to me what a Connect-Debounce is?  I may try to upgrade to 64bit Ubuntu as well since the error is supposed to be fixed in that version.

---

### Post by Endless_Nameless on 2010-03-01
The same here. I have a Vaio with Intel components, and today, after leaving the screen saver, no usb was working! I tried to reboot, with no success. In the first time, even the reboot would not work, it did not pass the bios screen, so I need to reboot again. 

I have dual boot with Windows, and for my horror the USB does not work in Windows too. It says that it could not recognize my ports.

even my built-in webcam stop working...

So, unfortunately, it is an Intel problem, but maybe related to Linux kernels, because if you look for this kind of problem, there are reports from years about, about the same thing happening.

I hope I can fix this, because an USB problem like this isn't something that technicians would solve, and if I have to change the computers, I will have to stop to use Linux, because it will be the second computer in less than 2 years that was physically and irreversible damaged by a kernel.:(

EDIT: I followed a suggestion that I saw in other place, and it worked! It is not a solution, but a "fix". Take off the battery and power cable, and let the computer rest for some time (in my case half hour). this seems to force the hardware to reset. After this, turn it on, and voilá! It acts like there was never a problem! I need to try again the same usb keyboard to see if the problem occurs again.
The person who suggested to do this said that some time later the problem appeared again, and it was treated the same way.

---

### Post by SaikoRonin on 2010-03-04
Unfortunately upgrading to 64 bit does not work either.  I will try to power cycle again..

---

### Post by Endless_Nameless on 2010-10-25
Wow, I forgot about this! 

I was about to reply to myself, because I did not remember that I already wrote here about this issue!

Again my computer had the same problem. Fortunately the fix that I used worked for all this time. Now I need to do it again.

I will try the new Ubuntu, or even some experimental things as Haiku. It would be worse if I thought that only Windows was good to it, but my wife has the same computer with Windows, and it went already 2 times to repair, because Windows destroyed the LCD screen and even the fan. Thesetype of Vaio (VGN) are not recomended by me!

---

### Post by lanetherif on 2012-06-26
It still persists and it is at the moment "Won't Fix" at launchpad. I faced it when I try to plug a -most probably- bricked mp3 player. Whoever the responsible part is, it is doing a great job; the bug has been first submitted in 2007.

---

