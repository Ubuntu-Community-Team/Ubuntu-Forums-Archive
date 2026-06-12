---
title: "logon via either serial or console"
date: 2010-11-11
forum: General Help
---

### Post by ilinktech on 2010-11-11
Hi,
 
Have used Linux for a number of years but new to Ubuntu and so far very happy with it. Using 10.10 server I have built a gateway system for one of my offices. The gateway does not require a login for it to work but the hard drive is encrypted and users at the office will need to enter the pre-boot passphrase anytime that the gateway is rebooted.
 
I've configured the grub file (/etc/default/grub) with the info that I have found in various online sources so that an end user at the office can get kernel messages, etc and enter the passphrase via a serial connection - here are the highlights of what I've set thus far:
 
GRUB_TIMEOUT=0
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX="console=tty0 console=ttyS0,115200n8"
...
 
No other changes to the grub file have been made and I have set up the getty file as directed. The serial connection works fine but here's where I run into a bit of an issue. The gateway is connected (via vga and USB) to an IP over KVM switch for management from our home office but it does not have a serial option - I can only access the console from the KVM. When I turn on the above settings, I can only enter commands (LUKS key, logon credentials, etc) via the serial connection; console appears disabled (I can see some messages on the monitor but there is no keyboard input). If I comment out the "CMDLINE_LINUX" and reboot, I can get to the console but cannot enter commands from the serial connection.
 
I have also tried putting the info shown "CMDLINE_LINUX" in "_LINUX_DEFAULT" (replacing "quiet") with the same results. This wasn't an issue when I was using CentOS for this type of system and I'm guessing that it is related to GRUB2 and I simply don't have it configured correctly (hoping, anyway). Is there anyway to have logon access for both the serial connection and the console?
 
Thanx a bunch...

---

### Post by ilinktech on 2010-11-12
Any thoughts? I can work around the issue by adding serial over ip equipment along with of the KVM but if I can avoid having to do that then it would be great.
 
Thanx...

---

### Post by TSJason on 2010-11-12
To me, it doesn't seem useful to encrypt the hard drive of a system that's functioning as a gateway. For the most part, such a system will be a base operating install and some customized configuration files so that it functions for your environment. I don't think there's a way around this beyond manual user intervention - and if there is then it seems that this would nullify the fact that the drive is encrypted anyway.

---

### Post by ilinktech on 2010-11-16
Hmmm....ok, maybe I didn't explain this clearly. The gateway has (in addition to the normal Ethernet connections) a serial connection to one of the office computers. If it has to be rebooted, then a user at the site enters the pre-boot passphrase via a terminal program on the workstation. Once the passphrase is entered, nothing else needs to be done - services that the gateway uses start and the office is connected to the WAN again.
 
This all works just fine - what I am looking to do (and have done in the past on other flavors of Linux) is have the ability for the local user to (when needed) enter that passphrase via the terminal program on the workstation and also have the ability for the remote admin to enter the passphrase via an IP/KVM switch. 
 
In most cases, I will never have to do this but for troubleshooting / upgrades I would rather have console access than doing it over SSH, etc and maybe getting into trouble without a way out (if you know what I mean). Having console access remotely ensures that if I pooch something on the gateway that I have "local" access at console 0 to fix the issue.
 
I have made a little progress - found that if I set the GRUB_CMDLINE_LINUX="" line to "console=tty1 console=ttyS0,115200n8" then although I still cannot enter the pre-boot passphrase from the IP/KVM, once the system fully boots I can login via the IP/KVM. This is better than nothing but it would still be nice to be able to enter the passphrase from either interface (console or terminal program via serial connection).
 
Hoping that explains it a bit more clearly - thanks again.

---

