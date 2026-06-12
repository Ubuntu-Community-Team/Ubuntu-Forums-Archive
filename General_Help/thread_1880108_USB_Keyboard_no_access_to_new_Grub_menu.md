---
title: "USB Keyboard no access to new Grub menu"
date: 2011-11-12
forum: General Help
---

### Post by L a r r y on 2011-11-12
Hello all,
I have installed this copy of Ubuntu off a 10.04 Live CD, complete with Grub 2 boot menu and ext4 filesystem.

I run a Windows computer on the other side of a usb kvm switch, but with that computer off line until I put a fan in it, the kvm switch is redundant.

The kvm switch required that I get a new USB keyboard, and so I am running a Gigaware keyboard with the switch.

The Grub menu is inaccessible through the switch with the USB keyboard, and today I determined that the keyboard is no better going direct for the Grub menu.

The menu works well with a PS/2 keyboard.

I don't know where I started a thread on this topic, I cannot find it.

I do have another one here about the failure to activate the kvm switch with the double-press of the scroll lock key.


Thanks in advance.

---

### Post by oldfred on 2011-11-12
I have had issues with KVM switches in the past but have not use one for years.

I did have the USB - PS/2 keyboard issue several versions ago just as I installed a new motherboard. It turns out that both Windows and Ubuntu load their own keyboard & mouse drivers but grub uses the BIOS setting defaults. I just had to turn on the USB keyboard setting in BIOS. 

Someone also mentioned there is now a usb_keyboard.mod and  a usb.mod  that you can load in grub2 to add a driver. But not sure how to enable that without keyboard working. I would think you have to add it to the grub menu from a liveCD which is not the easier, but can be done.

---

### Post by Cyclane on 2011-11-13
In a lot of BIOS menu's I've seen there's an option for USB keyboards. I believe it sets compatibility and has a few options, but I don't remember it very well (I'm at work at the moment). Go see if you can find it in your BIOS menu, it might help.

---

### Post by L a r r y on 2011-11-13
> **oldfred said:**
> I have had issues with KVM switches in the past but have not use one for years.

I did have the USB - PS/2 keyboard issue several versions ago just as I installed a new motherboard. It turns out that both Windows and Ubuntu load their own keyboard & mouse drivers **_but grub uses the BIOS setting defaults_**. I just had to turn on the USB keyboard setting in BIOS. 

Someone also mentioned there is now a usb_keyboard.mod and  a usb.mod  that you can load in grub2 to add a driver. But not sure how to enable that without keyboard working. I would think you have to add it to the grub menu from a liveCD which is not the easier, but can be done.

> **Cyclane said:**
> **_In a lot of BIOS menu's I've seen there's an option for USB keyboards_**. I believe it sets compatibility and has a few options, but I don't remember it very well (I'm at work at the moment). Go see if you can find it in your BIOS menu, it might help.

Thanks guys, that solved it!  In my copyright 2001 Award Software BIOS, under integrated peripherals support, is USB Keyboard support [Disabled].  I enabled that and my Grub 2 menu is accessible.

Thanks again.

---

### Post by L a r r y on 2011-11-13
I thought somewhere there was a "This post was helpful/ Thank you/ Add to my talkutation" sort of feature to credit posts that were helpful, but I don't see it.

A vote of thanks anyway to both posters here.

---

