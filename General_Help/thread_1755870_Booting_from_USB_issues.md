---
title: "Booting from USB issues"
date: 2011-05-11
forum: General Help
---

### Post by Cheetah05 on 2011-05-11
Hi there,

I have a joggler device and have Ubuntu installed on a USB drive. If that USB drive is the only thing plugged in it boots fine. If I plug another USB device it doesn't boot.

Now I am assuming this is a GRUB issue but I'm not really sure what to change and what I need to change it too.

I was told this by a friend: "probably need to change the grub.cfg where it states the boot device (hd0,x) etc".

How do I find out what I need to change it to?

Thanks.

---

### Post by hawthornso23 on 2011-05-11
Does it make a difference which way around the USBs are plugged in? 

The problem could be at BIOS level. The BIOS controls the boot sequence and may be set up to disable boot from USB when multiple devices are present.

---

### Post by Cheetah05 on 2011-05-11
It's off a USB Hub (there is only 1 USB port on the device). The USB drive works on its own (in the hub) but not if there is another device USB disk drive plugged in.

When I boot into Ubuntu and plug in another USB drive its fine.

---

### Post by Cheetah05 on 2011-05-11
This is the error I get:

```

Booting 'Ubuntu 11.04 (Natty) - 2.6.38.4joggler1'

error: unknown filesystem.
error: you need to load the kernel first.

Failed to boot both default and fallback entries.

Press any key to continue...

```

I can't press any keys as it is a touchscreen device.

---

### Post by Cheetah05 on 2011-05-12
This is what is in grub.cfg if it helps:

```

set timeout=2
menuentry "Ubuntu 11.04 (Natty) - 2.6.38.4joggler1" {
    set root=(hd0,1)
    linux /vmlinuz-2.6.38.4joggler1 root=/dev/sda3 ro quiet splash
    initrd /initrd.img-2.6.38.4joggler1
}

```

---

### Post by dragonfly41 on 2011-05-12
> 
It's off a USB Hub (there is only 1 USB port on the device). The USB  drive works on its own (in the hub) but not if there is another device  USB disk drive plugged in.I've found that USB hubs *if they don't have their separate power supply* can be problematic with USB drives.   Does your USB drive have a separate power supply?

If you only have one USB port make sure your USB hub is powered.

If you have multiple USB ports plug in your USB drive into the USB port nearest your power input (usually at rear of motherboard) since these ports can have a higher power drain.

Try your USB drive directly plugged in .. not through your USB hub .. to test this theory.

---

### Post by Cheetah05 on 2011-05-12
> **dragonfly41 said:**
> I've found that USB hubs *if they don't have their separate power supply* can be problematic with USB drives.   Does your USB drive have a separate power supply?

If you only have one USB port make sure your USB hub is powered.

If you have multiple USB ports plug in your USB drive into the USB port nearest your power input (usually at rear of motherboard) since these ports can have a higher power drain.

Try your USB drive directly plugged in .. not through your USB hub .. to test this theory.

Sorry I believe I made a mistake with my explanation.

I have two devices: 4GB Corsair Flash USB Stick & 1TB External 3.5" USB Drive (obviously plugged into mains aswell).

I have Ubuntu installed on the 4GB Corsair Flash drive.

When the 4GB Flash drive is plugged into the device on its own, IT WORKS.
When the 4GB Flash drive is plugged into the device via the USB hub, IT WORKS.
When the 4GB Flash drive is plugged into the device via the USB hub which also has the 1TB drive plugged in, IT DOES NOT BOOT (see above error).

Finally, if already booted when the 4GB Flash drive is plugged into the device via the USB hub AND THEN I plug in the 1TB drive, IT WORKS.

---

### Post by hawthornso23 on 2011-05-13
When more than one USB storage device is present, there is no easy way for the BIOS to determine which one to try to boot off. I could well imagine that in that situation it would simply skip USB boot altogether and try the next option in the boot sequence. The BIOS can't read the contents of a USB device to see what is on there. It doesn't have the required drivers to do that.  A BIOS is a pretty basic piece of software. It knows how to points at the boot sector of a device and initiate boot - and not much more. 

That is why I think this isn't an Ubuntu issue. Ubuntu isn't running when the problem happens. Before boot is initiated the BIOS is running the show. Make yourself a bootable USB key with some other operating system on it. I'm willing to bet that it will show exactly the same behavior. How can it be different? If the USB key hasn't been read then what is on it (ubuntu or dos or whatever) can't make a difference.

I suggest you go into your BIOS and check out what options it provides on the slim chance that it provides some kind of option to control this behavior. But I suspect you'll just have to live with it.

---

### Post by loseby on 2011-05-13
I actually went away from using GRUB and use the Motherboards commands...in my case F12 brings up the bootscreens options and when I want my Ubuntu USB Hard drive I just select the  + hard drive and then select the hard drive I want and in my case its the Samsunh 500 

If I want windows I just let it boot to windows

---

### Post by QLee on 2011-05-13
Cheetah05,
If your booting issue is caused by the situation that your external drive is enumerated first when it is connected, and that seems to be consistant with your description, then you might have success if you used the UUID of the device in your, "root=", line in the grub stanza for the usb stick that you want to boot. Even if the device node is different the system can find it by UUID.

---

### Post by Cheetah05 on 2011-05-13
Ah I have found my solution

So for anyone browsing that had the same situation as me this is what I did:

- Switched the devices around in the USB Hub.
- Changed "root=/dev/sda3" to "root=/dev/sdb3" in grub.cfg.


**Thank you to everyone for the guidance/responses**

---

