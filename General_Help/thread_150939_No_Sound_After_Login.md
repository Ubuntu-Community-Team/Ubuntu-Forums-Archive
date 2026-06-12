---
title: "No Sound After Login"
date: 2006-03-27
forum: General Help
---

### Post by omega13a on 2006-03-27
With the exception of the sound when I get when the log in screen shows up and the test sound I get in the Multimedia Systems Selector, I have no sound on my computer.  Can anybody help me get sound?

---

### Post by morpheus2485 on 2006-03-27
you should have a program called alsamixer installed on your computer, run it from the command line and try to adjust the volume

the arrow keys will raise and lower volume or switch to a different channel, and "m" mutes or unmutes.  

you can find out more information about alsamixer with 'man alasmixer' at the command line

if you get any errors when you try to run alsamixer copy and paste those errors here.

---

### Post by omega13a on 2006-03-27
I tried that this morning and again this evening and no luck.

---

### Post by JohnBoyJunior on 2008-07-12
I have the same problem - at first I had no sound so I did:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Then:
sudo apt-get install linux-sound-base alsa-base alsa-utils

Then I had to reload the desktop because removing the sound also seemed to remove the desktop!
sudo apt-get install gdm ubuntu-desktop

Now I get a login sound but nothing after that :confused:
Does anyone have any suggestions?

This is running on a Dell Dimension 4600 with CreativeLabs SoundBlaster Live

Thanks.

---

### Post by JohnBoyJunior on 2008-07-12
OK, this is a bit weird but after posting I was browsing the web and hit a page with a Flash movie that had some sound playing - and I could hear it! 

So I went back to Rhythm Box Music player and tried an MP3 player. Previously this didn't work but I could hear the tune playing. Yes! However...when I go to Sound Preferences > Sounds and try changing the System Sounds I don't hear them.

I'm not too concerned about that but this still seems a bit odd. I'll try a reboot and see if my sounds still work. If I don't post back then assume they do.

---

### Post by JohnBoyJunior on 2008-07-13
...and I boot up today and no sound again! This is getting silly.

---

### Post by zipperback on 2008-07-13
Please post for us the output of:  **lspci**


- zipperback
:popcorn:

---

### Post by JohnBoyJunior on 2008-07-13
Output from lspci:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:01.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
01:01.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
01:02.0 USB Controller: NEC Corporation USB (rev 43)
01:02.1 USB Controller: NEC Corporation USB (rev 43)
01:02.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

I'm running Ubuntu 8.04 installed using Wubi on a Dell Dimension 4600

---

