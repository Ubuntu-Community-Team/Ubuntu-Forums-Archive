---
title: "Startup disk"
date: 2011-04-12
forum: General Help
---

### Post by qkpony on 2011-04-12
Is there a way to make usb drives bootable with the startup disk creator in ubuntu that is not a ubuntu iso? I have a Backtrack Iso that I am wanting to make bootable from usb but it wont open in the built in startup disk creator. Or is there another way to do this?

---

### Post by mcduck on 2011-04-12
The Startup Disk Creator is intended only for Ubuntu disc images, and isn't any kind of generic tool for creating bootable USB drives.

You might have some lucky using [Unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by TeoBigusGeekus on 2011-04-12
> **qkpony said:**
> Is there a way to make usb drives bootable with the startup disk creator in ubuntu that is not a ubuntu iso? I have a Backtrack Iso that I am wanting to make bootable from usb but it wont open in the built in startup disk creator. Or is there another way to do this?

Consult your distro's documentation about how to create a bootable usb.
You could try with dd
```
dd if=/path/image.iso of=/dev/sdd bs=8M
```
Replace sdd with the proper device for your usb.
You might get lucky with this...

---

### Post by KegHead on 2011-04-12
Hi!

I've used netbootin for every flavor of iso.

It's in Ununtu Software center orsystwm...admin...synaptic.

KegHead

---

### Post by QLee on 2011-04-12
[QUOTE=qkpony]Is there a way to make usb drives bootable with the startup disk creator in ubuntu that is not a ubuntu iso? I have a Backtrack Iso that I am wanting to make bootable from usb but it wont open in the built in startup disk creator. Or is there another way to do this?[/QUOTE]

You might want to try the method recommended by the Backtrack site.
[http://www.backtrack-linux.org/tutorials/usb-live-install/](http://www.backtrack-linux.org/tutorials/usb-live-install/)

---

### Post by qkpony on 2011-04-13
Thanks guys I am trying Unetbootin

---

