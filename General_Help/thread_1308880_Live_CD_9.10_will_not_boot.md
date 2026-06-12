---
title: "Live CD 9.10 will not boot"
date: 2009-11-01
forum: General Help
---

### Post by historyb on 2009-11-01
Hello,

I tried the Live CD on two different computers and they did not boot, previous versions booted fine. Has anyone else encountered this behaviour?

---

### Post by QIII on 2009-11-01
It may be the disk itself.

Did you download it using a torrent client?

Did you burn the disk slowly?

Did you burn the disk as an .iso and not as a data disk?

Did you check the md5sum?

Did you run "Check disk for errors" from the LiveCD menu?

---

### Post by ankscorek on 2009-11-01
do the integrity check of the cd and the iso image

---

### Post by garvinrick4 on 2009-11-01
Something is wrong with cd.  burn another one.  

If you do not have a downloaded .iso image get one from
any ubuntu mirror and download to desktop. Then burn to a
cd.  at a medium speed.   

Takes about 12 minutes to get image downloaded if you pick a 
mirror with larger bandwidth. Lot of congestion on Ubuntu sites right now.

I believe there are 325 mirrors or so out there to pick from. 

Have a nice day.

---

### Post by historyb on 2009-11-01
> **QIII said:**
> It may be the disk itself.

Did you download it using a torrent client?

No, I didn't use a torrent

> **QIII said:**
> Did you burn the disk slowly?

Yes I did

> **QIII said:**
> Did you burn the disk as an .iso and not as a data disk?

As an ISO

> **QIII said:**
> Did you check the md5sum?

Yes, the md5 checked out on the ubuntu and kubuntu ISO

> **QIII said:**
> Did you run "Check disk for errors" from the LiveCD menu?

I tried and It just sits there with a blinking cursor up in the left hand corner

---

### Post by historyb on 2009-11-01
> **ankscorek said:**
> do the integrity check of the cd and the iso image

Did, the md5 checked out fine. This happened on the beta too, it worked in virtual box but not after being burned to CD.

---

### Post by starcraftmaster on 2009-11-01
make sure the bios is set to boot CDs

---

### Post by historyb on 2009-11-01
> **garvinrick4 said:**
> Something is wrong with cd.  burn another one.  

If you do not have a downloaded .iso image get one from
any ubuntu mirror and download to desktop. Then burn to a
cd.  at a medium speed.   

Takes about 12 minutes to get image downloaded if you pick a 
mirror with larger bandwidth. Lot of congestion on Ubuntu sites right now.

I believe there are 325 mirrors or so out there to pick from. 

Have a nice day.

Nope the CD's are good just loaded both into virtual box

---

### Post by historyb on 2009-11-01
> **starcraftmaster said:**
> make sure the bios is set to boot CDs

It is, it happens after I get to the grub screen and select to boot. Then it goes to a blank cursor and just sitting there blinking

---

### Post by ikacer on 2009-11-01
I saw some other posts of people with this problem. I don't know if there is a solution yet, but one person reported getting it to work by booting in safe graphics mode, so maybe you should try that. The thread I've seen about it is [http://ubuntuforums.org/showthread.php?t=1306277]("http://ubuntuforums.org/showthread.php?t=1306277")

---

### Post by historyb on 2009-11-01
> **ikacer said:**
> I saw some other posts of people with this problem. I don't know if there is a solution yet, but one person reported getting it to work by booting in safe graphics mode, so maybe you should try that. The thread I've seen about it is [http://ubuntuforums.org/showthread.php?t=1306277]("http://ubuntuforums.org/showthread.php?t=1306277")

Thank you, I tried that too no go.

---

### Post by retrow on 2009-11-01
You can boot the CD with other options than default. It would be especially helpful if you take out *quiet* from the boot options, that way you'll know which step is the installation flaking out at.

Here's a [guide on changing boot options]("https://help.ubuntu.com/community/BootOptions"), albeit from an older distro, but the interface is still the same.

---

### Post by historyb on 2009-11-01
> **retrow said:**
> You can boot the CD with other options than default. It would be especially helpful if you take out *quiet* from the boot options, that way you'll know which step is the installation flaking out at.

Here's a [guide on changing boot options]("https://help.ubuntu.com/community/BootOptions"), albeit from an older distro, but the interface is still the same.

I did try other options and it still will not go further, it flakes out after it detects the CD Drive than just sits there

---

### Post by bmbufalo on 2009-11-03
Just so you don't feel crazy this exact same thing is happening to me, has anyone found a fix? I've tried the x64 and x83 versions, nothing works.  Always boots to a cursor even when trying safe mode.

---

### Post by historyb on 2009-11-03
> **bmbufalo said:**
> Just so you don't feel crazy this exact same thing is happening to me, has anyone found a fix? I've tried the x64 and x83 versions, nothing works.  Always boots to a cursor even when trying safe mode.
I am glad that I'm not the only one. Hopefully there will be a fix soon

---

### Post by HegonBadde on 2009-11-04
I have the same issue.

I downloaded and burned the "ubuntu-9.10-desktop-amd64.iso" 3 different times from 3 different mirrors, all three have same issue.

**edit**
Removing quiet and or splash makes no difference
**end edit**

I took the same CD put it into a laptop and installed it to an external HD with no issues. (I could even boot off the external drive on the problem PC with no issues)

I'm currently running ubuntu 9.4 64bit on the problem PC
it's a Dell XPS 630i Intel Core2 Quad 2.4GHz, with 4Gig of Ram and a  Nvidia GeForce 88000GT Graphics card, and 2 sata hard drives
(contents of lspci pasted at bottom of message)

The live CD boots, the Language selection menu pops ups, and after that times out or I select english, I am presented with the option to Try it, install it, check the CD, perform memory test.

After I make a selection, The screen immediately goes black. a cursor appears in the upper left hand corner. The CD spins up. The fan spins up. The computer seems generally busy for about 30 seconds, then everything gets fairly quiet again, with no change, just the blinking cursor.

The screen makes no changes, it doesn't respond to any combination of ctrl + F1-9, ctrl + alt F1-9, ctrl + alt + del, ctrl + alt + back, or esc.

I've even left it alone for up to 2 hours (got distracted by a movie) 
to no effect.




Here's what lspci reports from the 9.4 install on the problem PC
**$ lspci**
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

---

### Post by kyuubi777 on 2009-11-04
i downloaded 9.10 as soon as it showed up on the site and for some reason the iso file size was around 555MB when the download finished...after i burned it, that CD did not boot up and instead read me errors, but i re-downloaded the iso file later and file size = around 668MB from what i remember... never had something like that happen before....just throwing it out there

---

### Post by historyb on 2009-11-04
> **HegonBadde said:**
> I have the same issue.

I downloaded and burned the "ubuntu-9.10-desktop-amd64.iso" 3 different times from 3 different mirrors, all three have same issue.

**edit**
Removing quiet and or splash makes no difference
**end edit**

I took the same CD put it into a laptop and installed it to an external HD with no issues. (I could even boot off the external drive on the problem PC with no issues)

I'm currently running ubuntu 9.4 64bit on the problem PC
it's a Dell XPS 630i Intel Core2 Quad 2.4GHz, with 4Gig of Ram and a  Nvidia GeForce 88000GT Graphics card, and 2 sata hard drives
(contents of lspci pasted at bottom of message)

The live CD boots, the Language selection menu pops ups, and after that times out or I select english, I am presented with the option to Try it, install it, check the CD, perform memory test.

After I make a selection, The screen immediately goes black. a cursor appears in the upper left hand corner. The CD spins up. The fan spins up. The computer seems generally busy for about 30 seconds, then everything gets fairly quiet again, with no change, just the blinking cursor.

The screen makes no changes, it doesn't respond to any combination of ctrl + F1-9, ctrl + alt F1-9, ctrl + alt + del, ctrl + alt + back, or esc.

I've even left it alone for up to 2 hours (got distracted by a movie) 
to no effect.




Here's what lspci reports from the 9.4 install on the problem PC
**$ lspci**
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

You made a great post, that explains the problem in a nut shell.

---

### Post by Larry Linux on 2009-11-05
Unfortunately, this is a big problem with many laptop installations using 9.10. There seems to be an Xorg problem relating to ACPI using Intel graphics.

What you need to do is the following...

When booting the live CD, when you reach the point where it asks if you want to install or run the live CD,...do this.

Press enter on F-6

In the right corner you will see "acpi=off"

Highlight "acpi=off" using the checkmark. This will turn off ACPI

The CD should then boot as normal.

But as a caution, turning off ACPI can mess with the power management of your computer and the cooling fan. Turning off ACPI is not meant to be a long term solution, but only a test. At this point, unless the bug is fixed, I would recommend using 9.04.

---

### Post by historyb on 2009-11-05
I'll try that, thank you. Mine that the CD did that on is a desktop, I have had to turn off ACPI a long time ago

---

### Post by historyb on 2009-11-05
That is exactly what it was. I turned ACPI off and Kubuntu finished booting up from the liveCD though it dumped me to a command line where I had to type startx

---

### Post by Larry Linux on 2009-11-05
> **historyb said:**
> I'll try that, thank you. Mine that the CD did that on is a desktop, I have had to turn off ACPI a long time ago

You're welcome. Please post back again with your results.

---

### Post by Larry Linux on 2009-11-05
> **historyb said:**
> That is exactly what it was. I turned ACPI off and Kubuntu finished booting up from the liveCD though it dumped me to a command line where I had to type startx

OK, now we're making progress;) As one other poster has suggested, perhaps the solution might be something as simple as updating the bios. I have yet to try that, but will soon. Perhaps you should as well. If an updated bios doesn't work, then we will know for sure that it's a bug coming from Ubuntu or the gnome developers.

---

### Post by historyb on 2009-11-05
Well Gnome can be elimanted since I had to do the same with Kubuntu. I'll have to get a floopy drive to update my bios, when I built my computer I left it out. :)

---

### Post by HegonBadde on 2009-11-05
Turning it ACPI off did not help me.

My problem PC is a desktop not a laptop (The lap top installed just fine).

The only option I can pick from the menu and not lock up with the blinking cursor is memory test.

---

### Post by HegonBadde on 2009-11-06
I've ran out of options to try.
Safe mode, each of the options from the f6, all the options from f6, combinations of f6 options.


Using the make USB startup disk and booting from that also hangs after I make a selection, but works fine on the laptop.


What kinda confuses me is that I used my laptop to install 9.10 onto an external drive. Which I can plug into the Desktop and it can boot the installed 9.10 just fine from that, it just can't boot the live-cd.


I guess the next thing is to see if I can clone the external Hard drive down to the desktop's  hard drive.

---

### Post by HegonBadde on 2009-11-07
Finally got it installed.

Installed 9.04 from scratch, (with ext4 partitions)
Pulled down all the updates.
Upgraded to 9.10

Everything is working fine.

---

### Post by historyb on 2009-11-14
Well I got an ubuntu CD in the mail today and the LiveCD boots to the login screen than wants a user name. I tried to hit enter, no go. I tried ubuntu as username and password still won't work, but at least I got to some kind of GUI

---

### Post by historyb on 2009-11-19
Anyone else getting this?

---

### Post by ankscorek on 2009-11-19
use acpi=off option

it will get u in

---

### Post by adroitster on 2009-12-23
Well the same problem is happening with my lenovo ideapad Y550 laptop. Everything worked well for sometime. I then booted up in the verbose mode (don't exactly remember what do you call it but it disabled the quite boot up option during the boot options in live cd). The messages gave me an idea about what was going wrong and I found that my hard disk was having problems.

Look for the following keywords in the messages during boot up and it will confirm that there is a problem with your HDD.
Buffer I/O error
DRDY ERR
Read fail on sector # blah blah
(you can figure out if there are other problems too)

With little googling I found that my HDD has to be replaced soon :(:confused:

---

