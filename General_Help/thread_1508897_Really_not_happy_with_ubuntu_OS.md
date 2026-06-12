---
title: "Really not happy with ubuntu OS"
date: 2010-06-13
forum: General Help
---

### Post by jamesa00789 on 2010-06-13
I switched from Windows Vista to Ubuntu 10.04 because I thought it was more stable, faster and more efficient at getting the job done but I have to say I am not impressed.

Several things do not work, and after browsing the forums I have failed to find a easy fix for each of them:

[LIST]
[*]Sleep and hibernate do not work
[*]Headphone jack does not work
[*]Brasero cannot burn DVDs
[*]When syncing iPod I get 100 or so error messages
[*]The theme keeps changing back to a really old basic version
[*]The speakers are very very crackly so I cannot listen to music
[*]I get randomly logged out
[/LIST]

Is anyone else having these problems after a fresh install of Ubuntu 10.04 or is it just my laptop?

Edit: also have these problems:

[list]
[*]Sometimes doesn't startup and just get some random text on the screen
[/list]

I am beginning to thing maybe my laptop isn't meant for linux

---

### Post by Monotoko on 2010-06-13
I'm not having any problems here and i think a lot of people can attest to this too..

Your laptop appears to be missing some important drivers, go to:
System -> Administration -> Hardware Drivers and see what it finds.

If it does not find anything, post the contents of the following command:
(Applications -> Accessories -> Terminal, then run the command and paste the output here)

```
lspci
```

---

### Post by techunit on 2010-06-13
> **jamesa00789 said:**
> I switched from Windows Vista to Ubuntu 10.04 because I thought it was more stable, faster and more efficient at getting the job done but I have to say I am not impressed.

Several things do not work, and after browsing the forums I have failed to find a easy fix for each of them:

[LIST]
[*]Sleep and hibernate do not work
[*]Headphone jack does not work
[*]Brasero cannot burn DVDs
[*]When syncing iPod I get 100 or so error messages
[*]The theme keeps changing back to a really old basic version
[*]The speakers are very very crackly so I cannot listen to music
[*]I get randomly logged out
[/LIST]

Is anyone else having these problems after a fresh install of Ubuntu 10.04 or is it just my laptop?
The problem you are experiencing is not typical of a normal users experience and you need to provide some information regarding your system so we can tell you what you need to do so you can get the most out of the experience. Ubuntu 10.04 is incredibly stable and I never have problems with the OS that I don't do to myself (I like to tinker)

So can we have the system specks on your system and the cercumstances you installed it under.

---

### Post by jamesa00789 on 2010-06-13
Hi, Thanks for getting back. If Ubuntu 10.04 is stable, why am I and other people getting problems? I have done many installations of Windows in many boxes, and had no problems. Basically all I want is something that works!

Anyway, here is what I get:

```
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
```

I was originally using Kubuntu, but after several problems such as programs (eg Dolphin) kept on crashing all of the time (and sleep and hibernate did not work) I erased the partition and did a fresh install of Ubuntu 10.04.

I have attempted at installing the propriety driver for the Ati Radeon graphics card, but it gave me some error and I just didn't have the time to sort it out.

I have reinstalled all the Alsa drivers and I still cannot listen to music via headphones. The music is very crackly, which it wasn't when using vista so it definitely isn't my speakers.

Any help would be great before I change back to windows :( :(

---

### Post by hhoyt on 2010-06-13
I put a dell studio laptop on 10.04 *BETA* and never had a problem.
Suspect it has to be your drivers.

Howard

---

