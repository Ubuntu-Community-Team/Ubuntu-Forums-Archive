---
title: "no sound with Kaemic/Lucid (Intel soundcard)"
date: 2010-03-26
forum: General Help
---

### Post by tzury on 2010-03-26
I got Intel sound card on board but it is not producing any sound.
dumping below my `lspci` results
thanks in advance for your help

```

$ lspci 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:05.0 Ethernet controller: Alteon Networks Inc. AceNIC Gigabit Ethernet (rev 01)
02:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

```

---

### Post by Boobek on 2010-03-27
I have the same problem except my machine (lucid 10.04) play sound when i put my headset in.

Do you have sound when you plug in your headset?

edit:
I'm solving my problem temporary.
Try this:
install linux-backports-modules-alsa-lucid-generic 
If that package isn't avaiable then install "linux-backports-modules-alsa-\\\\biggest version\\\\-generic"

after this step you must restart your system and boot with the kernel version "\\\\biggest version\\\\"

And now: sounds hearing fine.

---

### Post by tzury on 2010-04-02
> **Boobek said:**
> 
Try this:
install linux-backports-modules-alsa-lucid-generic 


Just did the following:
```
sudo aptitude install linux-backports-modules-alsa-lucid-generic 
```

Got this as a result, 

```

The following NEW packages will be installed:
  linux-backports-modules-alsa-2.6.32-19-generic{a} 
  linux-image-2.6.32-19-generic{a} 

```
confirmed and installed, rebooted as well. However, no menu on grub to select a specific kernel. and no sound after restart.

---

### Post by Muscovy on 2010-04-05
You can pick a kernel by holding ESC (escape) before the splash start.

I'm curious if I can get it working. I don't have enough space on the live boot to try now. It's a Windows (:neutral:) computer, but I highly suspect the users will get it nice and messed up if they keep up their security practices. I was hoping Linux would work on this machine.

---

### Post by Boobek on 2010-04-05
> **Muscovy said:**
>  I was hoping Linux would work on this machine.
It's a big question;)
Try it on 'live mode' without installation and you see what hardware is working and what is not. 
I think ALSA back-ports solving all Intel sound problem, so it isn't bundled with this question.

---

### Post by emreesen on 2010-05-01
> **tzury said:**
> Just did the following:
```
sudo aptitude install linux-backports-modules-alsa-lucid-generic 
```Got this as a result, 

```

The following NEW packages will be installed:
  linux-backports-modules-alsa-2.6.32-19-generic{a} 
  linux-image-2.6.32-19-generic{a} 

```confirmed and installed, rebooted as well. However, no menu on grub to select a specific kernel. and no sound after restart.

This solution solve my problem after rebooting all I had to do is unmute the speaker from the panel.
Thanks.

---

### Post by dino99 on 2010-05-01
you need to install paprefs and gnome-alsamixer (tweak settings into "apps -sound-gnome-alsamixer menu)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

