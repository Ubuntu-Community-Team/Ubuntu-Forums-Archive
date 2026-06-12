---
title: "NO SOUND on Eee PC 1101HA"
date: 2010-03-10
forum: General Help
---

### Post by GorgeousGe0rge on 2010-03-10
Hello Avid Ubuntu Users!

I'm relatively new to Linux and have settled upon Xubuntu.  I use Karmic Koala, and for the most part really love it.  I'm an inexperienced beginner with Linux and still riding the learning curve.

I am, however, still having issues with the operating system: namely with sound.  In the beginning after the 184 updates and solving the screen resolution issue, I found that I had [COLOR=Red]***NO SOUND***[/COLOR] :( despite the fact that video runs like a dream.

About a week after installation, I found that I had sound :D. I then proceeded to solve the screensaver issue by removing the Gnome screensaver and installing xscreensaver.  After this, [COLOR=Red]***AGAIN NO SOUND***[/COLOR]!! :neutral:  (I'm not sure whether solving the screensaver issue has affected the sound that I'd previously had.)

I also use the KFCE desktop.
[COLOR=SeaGreen][I][B]
[COLOR=Green]If there is anyone who has experienced this or knows how to solve this issue or even refer me to the appropriate post, I would be most gratefu[/COLOR][/B][COLOR=Green]**l.**[/COLOR][/I][/COLOR]

Best regards:

GorgeousGe0rge



Below are the specs for my netbook if it's of any use:


Notebook

product: 1101HA
vendor: ASUSTeK Computer INC.
version: x.x
serial: 97OAAS432450
width: 32 bits
capabilities:
    SMBIOS version 2.5,
    DMI version 2.5,
    SMP specification v1.4,
    Symmetric Multi-Processing
configuration:
    boot: normal
    chassis: notebook
    cpus: 1
    uuid: 807F9F81-02E6-4581-37D7-002618913AB2

gorgeous_george@Xubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

---

### Post by Gallienus on 2010-03-10
Hi George,

You might like to look at the following thread.

[http://ubuntuforums.org/showthread.php?t=1263644](http://ubuntuforums.org/showthread.php?t=1263644)

The sixth post has one possible solution.

(Guess who... :) )

---

### Post by GorgeousGe0rge on 2010-03-10
Thanks!  I'll have a look ;)

May the Force be with you...

---

### Post by GorgeousGe0rge on 2010-03-10
I tried the script from the sixth message of that thread and have sound now =D>

Kudos to you, Mr Gallienus!

We'll see if it (the sound) lasts after a few more re-boots...

Best

---

### Post by GorgeousGe0rge on 2010-03-11
Well...it's been 8 hours since the last post and I still have sound!!  [COLOR=Red]_**BUT**_[/COLOR] when I use the headphone jack, the speakers don't cut out.  Not very convenient!

However, I'm very pleased that I have sound again. :D

Need to solve this speaker-not-cutting-out issue... :-\"

---

### Post by kio_http on 2010-03-11
I had the same problem on Kubuntu on the same machine. However I fixed it by installing pulseaudio.

Note: Pulseaudio is a KDE module and may not work in Xubuntu. however you can try

```
sudo apt-get install pulseaudio
```

---

### Post by GorgeousGe0rge on 2010-03-12
Hi Kio:

I avoided pulseaudio on the basis of the vast majority of negative comments about it, so I followed some other advice and got the desired result(s... eventually...:p)

---

### Post by kio_http on 2010-03-12
> **GorgeousGe0rge said:**
> Hi Kio:

I avoided pulseaudio on the basis of the vast majority of negative comments about it, so I followed some other advice and got the desired result(s... eventually...:p)

True I heard negative comments about it. However for most of my pc's installing pulseaudio makes things better and fixes sound conflicts with virtualbox etc.

Could you please post what your "other means" are?

---

### Post by GorgeousGe0rge on 2010-03-15
Kio:

Other means: have a look at message #2 in this thread...

---

