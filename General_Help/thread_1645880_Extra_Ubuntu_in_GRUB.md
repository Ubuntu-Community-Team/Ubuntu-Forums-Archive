---
title: "Extra Ubuntu in GRUB"
date: 2010-12-15
forum: General Help
---

### Post by Zeophlite on 2010-12-15
I was successful in getting my wifi to work in 10.10, so first thing, I opened Update Manager and updated everything.  Once that finished, I restarted and grub had 2 new Ubuntu options.  I hit e to check and they are the same, besides the 23 and 22

```

GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-23-generic
Ubuntu, with Linux 2.6.35-23-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
followed by Memory tests, and Windows 7

```

The first ubuntu (23) does not have my wifi working, and the third (22) does.  How do I remove the first one, and whats the difference between the two?

Cheers

---

### Post by Rubi1200 on 2010-12-15
Try running ```
sudo update-grub
``` and see if it makes a difference.

---

### Post by Zeophlite on 2010-12-15
Ah, apologies, it seems I misread GRUB, the two are different.
One is 2.6.35-23, the other is 2.6.35-22.  22 has wifi working, and 23 does not

---

### Post by Rubi1200 on 2010-12-15
No problem :)

Whenever there are kernel upgrades, a new entry is added to the GRUB menu.

Most experienced users will advise you to keep at least one spare in case you need to troubleshoot issues with an upgrade.

In other words, your setup is fine (aside from the wifi issues of course).

Hope this helps.

---

### Post by coffeecat on 2010-12-15
If wi-fi is working with the older kernel and not with the newer it sounds as though you had to compile a driver against the kernel when you were getting the wireless to work. If this is so, you will have to go through the compile steps again, only this time with the new kernel. This is the disadvantage of compiling your own driver.

Out of interest, what wireless device do you have, and what did you do to get it working? I ask because I wonder why you resorted to a self-compile. This is sometimes needed, but perhaps there might be an easier way for you.

---

### Post by Zeophlite on 2010-12-15
Okay, so how do I get wifi to work in the new one?  Why didn't it carry over from the old one?

Update's aren't working in the old one (fails when I click Check), and new doesn't have wifi, so I can't see if it works there?

---

### Post by Zeophlite on 2010-12-15
Ah coffeecat, that makes sense, I did self compile.
I self compiled because it was the only option I knew of.

Basically I did this (first post):
[http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)
Followed by this (first post on page):
[http://ubuntuforums.org/showthread.php?t=1444925&page=2](http://ubuntuforums.org/showthread.php?t=1444925&page=2)
But in more detail (and as far as I can tell - I can't remember the exact order as I tried multiple things, deleted, retried, etc):

My card is a Tenda W322P V2.0 PCI Wireless-N.  lspci tells me that its a RaLink Device 3062.
From [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) I downloaded RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592) , extracted, checked on the Makefile that "MODE = STA" and "TARGET = LINUX", then modified os/linux/config.mk such that:
HAS_WPA_SUPPLICANT = y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y

sudo make
sudo make install

Possibly ran
insmod rt2870sta.ko
in os/linux,


Added to /etc/network/interfaces :
auto wlan0
iface wlan0 inet dhcp


Added to /etc/modprobe.d/blacklist.conf :
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

(I think I choose them from
dmesg | grep rt2
dmesg | grep rt3
)

Added to /etc/modules :
rt3062sta



Then restarted.

But like I said, I'm not sure what made it work!




If I boot in 23, sudo make, sudo make install, would that be sufficient?  Would that interfer with 22's wifi?

---

### Post by ajgreeny on 2010-12-15
> **Zeophlite said:**
> Okay, so how do I get wifi to work in the new one?  Why didn't it carry over from the old one?

Update's aren't working in the old one (fails when I click Check), and new doesn't have wifi, so I can't see if it works there?
What do you mean by "Updates aren't working in the old one"?

The old one and the new one are not two different operating systems, just different kernels in the same OS; you pick the kernel you want to use from the grub menu.

What is obviously needed is more information on your wifi hardware, we can then perhaps get your new kernel working wifi, and you should be good from then on.  Can you copy back here the output of ```
lspci
``` in terminal, please as it may help to show us your wifi card.  If it's a usb card let's see the output of ```
lsusb
```

---

### Post by coffeecat on 2010-12-15
> **Zeophlite said:**
> If I boot in 23, sudo make, sudo make install, would that be sufficient?  Would that interfer with 22's wifi?

It shouldn't. What you are doing is compiling kernel modules which are not present in the packaged kernel. For -22, they would have gone somewhere in /lib/modules/2.6.35-22-generic/ and would be unavailable to the -23 kernel. What you need to do is to boot into the -23 kernel and follow all the compile steps again. Then a new wireless module driver will be created and put into /lib/modules/2.6.35-23-generic/. Thus you will have a wireless driver for each version of the kernel.

You will have to do this each time the kernel is upgraded. At least until you find an easier way to do this.

---

### Post by Zeophlite on 2010-12-15
> **Zeophlite said:**
> 
My card is a Tenda W322P V2.0 PCI Wireless-N.  lspci tells me that its a RaLink Device 3062.


Apologies for my poor language in my previous post, I was not sure how to word it, as I did not quite understand it.

By "old one" I simply mean when I pick Ubuntu, with Linux 2.6.35-22-generic from GRUB and "new one" I mean Ubuntu, with Linux 2.6.35-23-generic.

By updates aren't working, I mean that despite the internet working in Linux 2.6.35-22-generic (Firefox loads a page), when I open Update Manager the click Check I got several failed messages.  Strangely it is working now, so maybe that was a temporary problem.

> **Zeophlite said:**
> 
If I boot in 23, sudo make, sudo make install, would that be sufficient? Would that interfer with 22's wifi?


So my thesis is, if I booted Linux 2.6.35-23-generic , ran the above commands, is that all that's necessary?  I wanted to ask first before I attempted in case it caused a problem with Linux 2.6.35-22-generic access of the wifi.

---

### Post by Zeophlite on 2010-12-15
Thanks coffeecat, I'll try now and report back.

---

### Post by Zeophlite on 2010-12-15
Booted into 23, ran
sudo make
sudo make install
Restarted, booted into 23, wifi works, restarted, booted into 22 and wifi works.

I'll keep 22 as a back up, in case of any nasties, but for the record, how do I remove that kernel?

---

### Post by Zeophlite on 2010-12-15
Also seeing as I've figured out how to get it to work, can I somehow report this to Ubuntu people to add it to the standard?  (excuse my clumsy wording, I'm unsure of how to refer to it)

---

### Post by coffeecat on 2010-12-15
> **Zeophlite said:**
> I'll keep 22 as a back up, in case of any nasties, but for the record, how do I remove that kernel?

It's a good idea always to keep one recent version of the kernel in case of other problems with the latest. When you get an unwieldy collection, simply search for the '2.6.35-22' string in Synaptic and uninstall the 3-4 packages the search throws up. That will remove the modules you have created and will cause the grub menu to be regenerated so that you don't see the uninstalled kernel in it.

> **Zeophlite said:**
> Also seeing as I've figured out how to get it to work, can I somehow report this to Ubuntu people to add it to the standard?  (excuse my clumsy wording, I'm unsure of how to refer to it)

I'm not sure what you mean, but if you mean the  need to recompile a module when you install a new kernel, then don't bother. This is not a bug; it's simply a product of the way the Linux kernel and its module/drivers work. The need to recompile a kernel module is well known and Linux users have been doing this since the kernel was a glint in Linus' eye. :wink:

This is the advantage of having hardware that is supported by the stock kernel. All this is taken care of by the package maintainers each time a new kernel appears in updates. In fact, if you're lucky, you might find a future kernel upgrade causes your wireless to work without you having to go through all this. If this happens, that means that the wireless driver has been incorporated into the kernel for you.

---

### Post by Zeophlite on 2010-12-15
Ah so since the source to this driver is available, can I somehow bug someone into making the stock kernel be able to support it?  Or am I being greedy :p

In all seriousness, how is it decided what goes in and what stays out?  I realise I'm way off topic here, so this is my last question, I swear

<_<

>_>

---

### Post by coffeecat on 2010-12-15
The driver will find its way in in due course once it's passed whatever testing is needed, but perhaps not for the release you are using, Maverick. I notice you are using a ralink chipset, but it must be one of the newer ones if there isn't a working Ubuntu kernel driver. The one problem with Ubuntu is that a kernel version is fixed in a particular release of Ubuntu. That is, Maverick will always have the 2.6.35 kernel, whatever is released upstream. You will get bugfixes and perhaps some backported stuff, but you won't get a newer kernel. For instance, the in-development Natty/11.04 release is using the 2.6.37 kernel at the moment, but the only regular way that you will get the 2.6.37 kernel is by upgrading to Natty once it goes final. You can install a newer kernel to an older Ubuntu release, but I wouldn't recommend it unless you are experienced.

But there is one thing you might want to try when kernel 2.6.35-24 (or higher) is made available in the updates. Don't do this for your present kernels - you have a working driver already. After you've installed the 2.6.35-24 kernel, don't compile your driver as you have done before - at least not at first. Go to the Synaptic package manager and install the package linux-backports-modules-wireless-maverick-generic. That will install a number of wireless drivers backported from a newer version of the kernel but compiled to work with the present one. If you are lucky it will include a working driver for your wireless device. If you are unlucky, all you have to do is compile your driver as before.

When Natty is released next April, download the desktop ISO and try the live CD. See if wireless works for you. Hopefully, it will.

Good luck!

---

