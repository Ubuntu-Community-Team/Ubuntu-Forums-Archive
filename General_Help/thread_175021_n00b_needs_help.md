---
title: "n00b needs help"
date: 2006-05-12
forum: General Help
---

### Post by Just.Me on 2006-05-12
[B]Hey all,

I am a complete beginner to ubuntu and just love it already. I have figured out the most myself, but there are a few annoying options remaining :( .

1.Synaptic can't seem to find some of the prgrams I need (for example Xinerama).
Am I just overlooking something or missing some repositories?
Here is my sources.list:[/B]

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

[B]2.I am running on a NVIDIA GeForce4 Ti 4600 and already installed the drivers succesfully. This is a dual head card, but I can't seem to let it run with a dual head setup. My first problem is that I'm not sure if Xinerama is installed, because I can't find it in Synaptic (see above). My second problem is that I don't seem to have two separate pci adresses for both of my monitors when I run lspci. When I try to setup xorg.conf, I seem to need two separate pci adresses (or is this something I just made up?)
This is my lspci output:[/B]

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0080 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0084 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 0088 (rev a2)
0000:00:04.0 Bridge: nVidia Corporation: Unknown device 008c (rev a3)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 008a (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation: Unknown device 008b (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation: Unknown device 0085 (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

[B]3.My sound and especially my bass is racking up. I really don't have a clue how to figure this one out. Is it something with the driver or the config file?

4.When I made a clean install of ubuntu, nautilus detected without a problem my entire (windows) network. [I just love ubuntu!!!] But since I installed samba to share my files with other computers, nautilus asks for a network authentication. How can I disable this, because I can't browse my network. I think it's somewhere deep down in a config file of samba which I haven't found.

It would be really great if some of you would be so nice to help me out, even if it is with a faint idea about what is going on.

Thanks in advance

Complete n00b[/B]

---

### Post by IYY on 2006-05-12
> 1.Synaptic can't seem to find some of the prgrams I need (for example Xinerama).

Xinerama should be on your system by default.

> 2.I am running on a NVIDIA GeForce4 Ti 4600 and already installed the drivers succesfully. This is a dual head card, but I can't seem to let it run with a dual head setup. My first problem is that I'm not sure if Xinerama is installed, because I can't find it in Synaptic (see above). My second problem is that I don't seem to have two separate pci adresses for both of my monitors when I run lspci. 

NVIDIA cards work much better with TwinView rather than Xinerama. There are several sample xorg.conf files on these forums to show you how to configure it.

---

