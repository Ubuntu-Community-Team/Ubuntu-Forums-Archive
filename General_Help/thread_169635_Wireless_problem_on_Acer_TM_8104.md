---
title: "Wireless problem on Acer TM 8104"
date: 2006-05-03
forum: General Help
---

### Post by jameskhoo on 2006-05-03
Hi all gurus..

I am currently running on Ubuntu Breezy Badger 5.10 on my Acer TM 8104, kernal image 2.6.12-10-386. I have install the ubuntu base on this [guide]("http://www.hld.ca/?p=24"), and perform and update after installation, everything work fine (including the power management ACPI module) , except the wireless card. For some unknown reason, the wireless card (ie. ipw2200) refuse to turn on, no matter how hard or how many times I press the front wireless button, it just refuse to turn on...

Switching back to devil Windows XP, everythings work fine.

Here's a listing on my boot parameters in grub/menu.1st:
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/sda6 ro noapic noacpi quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot


Here's my "lshw" on the wireless setting:
          *-network:0 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2915ABG MiniPCI Adapter
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@06:03.0
                logical name: eth0
                version: 05
                serial: 00:12:f0:a4:41:99
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 multicast=yes wirele

As u can see the network is disabled...any where to enable it back?

Any help/pointers is appreciated, thanks

James Khoo

---

### Post by jameskhoo on 2006-05-07
Hi all

Just Bump to see if anyone knows how to resolve my issue.
On the other hand, if anyone have a custom DSDT that work "out of box" (For Power management and Wifi) for Acer Travel Mate 8104 with 1.5 GB Memory..could u please please share with me..thanks

James Khoo

---

### Post by cuboconojos on 2006-05-07
Hi, James! Look, I had the same problem. I even had to do the sadest thing:
turn on the laptop on Windows, so the card could turn on and then restart to
Linux... everytime I wanted to use my laptop!!!
Well, I'll go to the point! Ubuntu can't control the wireless button on your laptop, you need an extra driver called acerhk... the good news are that Breezy has it! You just have to load it like this:

> $sudo modprobe acerhk usedritek=1 autowlan=1 force_series=290

(to load the module)
NOTE: If anybody else reading this doesnt have acerhk, ge it [here](http://www.informatik.hu-berlin.de/~tauber/acerhk/).

and then you actually turn it on:

> $sudo echo 1 > /proc/driver/acerhk/wirelessled

and enjoy!! Hope it works for you.
Oh!, since you'll be doin this everytime you turn on the laptop, it ould be nice to write a little script with this lines:

1.Create a file called cardON (for example).
2.Write this on the file:
> #/bin/bash

modprobe acerhk usedritek=1 autowlan=1 force_series=290
echo 1 > /proc/driver/acerhk/wirelessled

3.Save it and give exec permits with:
> $chmod a+x cardON
4.Then everytime turn on your laptop you go:
> $sudo ./cardON

Well that's it! And remember... if that dumb Windows can do it, so can Linux!
Greetings from Chile!

---

