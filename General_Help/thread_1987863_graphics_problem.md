---
title: "graphics problem"
date: 2012-05-26
forum: General Help
---

### Post by EvilTesla on 2012-05-26
I have recently started using Ubuntu, and so far I have found it much easier to use than windows.
 
However, this morning I turned on my computer, letting it boot to Ubuntu 12.04, and instead of booting like it normaly does, it booted to a comand prompt.
 
This concerned me a little, and so I tried typing "nautilus" and "gnome" trying to get the display to start. Both times it gave me an error saying something along the lines that the display is not found.
 
 
I tried then booting in graphics safe mode, and it gave a screen of text, and returned to the safe boot menu without booting up. The text was only up for a short period of time, so I wasn't able to read most of it.
 
I did get down a line "Screen(s) found, but non have usable configuration"
 
I suspect what happend is that some update (or something) messed with my screen configuration, and now I have no idea how to fix it.
 
 
 
I also have a few other minor questions and problems, but I'll wait till I can get this resolved to bring them up.
 
 
currently I am running my windows boot (THE PAIN!!), which is working just fine, so I don't think it is a hardware problem. 
 
 
Thanks!
Brian Hare

---

### Post by Zvlwab on 2012-05-26
There should be a line saying:
```
Ubuntu ...bla... tty7
```
If the last number is not a 7, try pressing CTRL+ALT+F7

Else try this:
```
sudo lightdm
```

---

### Post by Jimmyfj on 2012-05-26
At the prompt you need to login with your usual username and password.
Having done that you need to get into administrator level. Youdo that by typing:

```
sudo su
```

and then you enter your login-password. This will not be shown as you type, for security reasons.

When in administrator condition you type

```
gdm
```

If that doesn't work try typing:

```
startx
```

---

### Post by gnusci on 2012-05-26
type the command

$ lspci

and post the output.

---

### Post by QIII on 2012-05-26
Please do as gnusci requested.  That is where diagnosis begins.

But I'd like to make a couple of clarifications.

There is no reason to use sudo su here.

The command would be
```
sudo service gdm start
```

Or

```
sudo start gdm
```

---

### Post by EvilTesla on 2012-05-26
I tried what Zvlwab said, and neither worked.
It was running in tty1, so I hit ctrl-alt-f7,  and the computer stopped at after printing line:
"starting automatic crash report generationsing daemonpatcher"
 
after re-booting I tried sudo lightdm,
which also stopped after printing line:
"starting regular background background program processing daemonpatcher"
 
 
now I'll try   lspci  and  sudo start gdm  and see what happens,

EDIT:

lspci gave:

00:00.0 Host bridge: intel corporation core processor DRAM controller (rev12)
00:01.0 PCI bridge: intel corporation core processor PCI Express x16 root port (rev 12)
00:1a.0 USB contoller: intel corporation 5 series/3400 series chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Inetl Corporation 5 series/3400 series chipset High definition audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 series/3400 series chipset PCI express Root port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 series/3400 series chipset PCI express Root port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 series/3400 series chipset PCI express Root port 4 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 series/3400 series chipset PCI express Root port 5 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 series/3400 series chipset PCI express Root port 8 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 series/3400 series chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge:  Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge   Intel Corporation Mobile 5 series chipset LPC Interface Controller (rev 06)
00:1f.2  STA controller: Intel Corporation 5 series/3400 series chipset 6 port SATA AHCI controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 series/3400 series chipset SMBus controller (rev 06)
02:00.0 VGA compatible controller: advanced micro devices [AMD] nee ATI broadway XT [Mobility Radeon HD 5800 series]
02:00.1  Audio device: Advanced Micro Devices [AMD] nee ATI juniper HDMI Audio [Radio-----series]
03:00.0 Network controller: Realtek semiconductor co., LTD RTL8191SEvB wireless LAN controller (R10)
07:00.0  Ethernet controller: realtek semiconductor co., RTL8111/8168B PCI express gigabit ethernet controller (rev 03)
09:00.0  firewire (IEEE 1394): Jmicron technology corp. IEEE 1394 Host Controller
09:00.1 system peripheral: Jmicron technology corp. SD/MMC Host Controller
09:00.2 SD Host Controller: Jmicron technology corp. standard SD Host Controller
09:00.3 system peripheral: Jmicron technology corp.   MS Host Controller
ff:00.0   host bridge: Intel Corporation Core Procesor QuickPath Architecture Generic Non-core registers (rev 02)
ff:00.1  host bridge: Intel Corporation Core Procesor  quickpath architecture system address decoder (rev 02)
ff:02.0 host bridge: Intel Corporation Core Procesor   QPI Link 0 (rev 02)
ff:02.1 host bridge: Intel Corporation Core Procesor   QPI Physical 0 (rev 02)
ff:02.2 host bridge: Intel Corporation Core Procesor reserved (rev 02)
ff:02.3 host bridge: Intel Corporation Core Procesor reserved (rev 03)
 

q1: how do I do the code wrapper?
q2: to get this I had to transcribe it by typing it into a different computer, is there a better way to to do this?


I also tried "sudo start gdm"  and it said something about not recognizing the comand for gdm.

thanks!

---

### Post by gnusci on 2012-05-26
From the command line remove the xorg.conf and reboot

$ sudo rm /etc/X11/xorg.conf
$ sudo reboot

Check this post

[http://ubuntuforums.org/showthread.php?t=1814871](http://ubuntuforums.org/showthread.php?t=1814871)

---

### Post by EvilTesla on 2012-05-26
> **gnusci said:**
> From the command line remove the xorg.conf and reboot
 
$ sudo rm /etc/X11/xorg.conf
$ sudo reboot
 
Check this post
 
[http://ubuntuforums.org/showthread.php?t=1814871 ]("http://ubuntuforums.org/showthread.php?t=1814871")
 
no good.
I'll try the driver thing tomarow

---

### Post by QIII on 2012-05-27
Please have a look at the ATI driver link in my signature.

---

### Post by EvilTesla on 2012-05-27
IT LIVES!!!  thank you very much for your help. I installed the ATI driver via Q111's instructions, and now the display is working as it should.

---

