---
title: "Move harddisk with Ubuntu"
date: 2012-02-03
forum: General Help
---

### Post by cokicd on 2012-02-03
I've just bought a new computer, I already have an ubuntu installation on my old laptop's hard drive. The question is, what happens if I connect the laptop's hard drive to my new computer and try to boot ubuntu from there?, will it work just like it did on the laptop?

Thanks

---

### Post by searchfgold6789 on 2012-02-03
Yes, it will work. One of the things I love about linux lol.
You might have to configure graphics a bit, but chances are you'll get to a desktop.

---

### Post by grahammechanical on 2012-02-03
I would add this.

How old is the Ubuntu? How new is the new machine's hardware? If you are up to date with Ubuntu then it should cope with the latest hardware. Although Linux is always a little behind when it comes to hardware. Older versions of Ubuntu might not be too comfortable run CPUs that were developed after the version was released.

Regards.

---

### Post by Bucky Ball on 2012-02-03
All configuration (hardware drivers) will be for your old computer; motherboard, processor, and not just graphics. I really have my doubts. It may work but with a little or considerable amount of tweaking.

---

### Post by WorMzy on 2012-02-03
It'll probably work, but if the default kernel+initrd doesn't, try the default kernel+fallback initrd. That'll autodetect the changes in hardware; once it's booted, run mkinitramfs (I think that's what Ubuntu uses) to generate a new initrd. After that, the default kernel+initrd should work again.

---

### Post by yetiman64 on 2012-02-03
The only thing I've ever had trouble with when switching an install between an AMD X4 processor based m/board and an Intel core2duo (T2500) based laptop is the graphics drivers.

This is using an install of 10.04 on the laptop HDD, then transferring it to an external dock (has both usb2 and e-sata connectors) for use with the desktop. All hardware seems to be automatically detected and modules changed to suit the new system. However the difference between the graphics modules when using proprietary drivers causes "low graphics mode" on startup.

If you have the same brand (Nvidia, ATI, Intel) graphics cards in both setups, you will likely not have a problem. I have booted my HDD on other laptops with NVidia cards (same as my tower setup) without any problems at all - didn't even need to use recovery mode to fix the graphics drivers in that case.

If you do have boot problems after a change I'd suggest you try out what WorMzy posted. I've not had a problem like that at all ever, but dependent on your hardware I suspect it is possible.

---

### Post by cokicd on 2012-02-04
The old hardware was intel core2duo, nvidia card. New hardware is i5 2500k, intel card.
I'll try today to see what happens

Thanks

---

### Post by cokicd on 2012-02-04
Well, it worked. It showed an error about NVidia drivers, and started in low graphics mode.
how can I reconfigure the graphics to support the intel card?

thanks

---

### Post by Bucky Ball on 2012-02-04
Do an update. Check 'Additional Drivers' (or 'Hardware Drivers' depending on the release).

---

### Post by llamabr on 2012-02-04
What you did barely worked, and the way you're trying to do it is the long way around.  Your initial installation was specific to your hardware of your laptop.  That's part of what happens during an install.  The software that's running on your desktop is configured for your laptop.  This may even include temperature and fan controls, and other important things you won't see until it melts.

So now you can begin to edit every config file, or you can just do it the right way around the first time, and do a fresh install.  That's what the installation procedure is for.

---

### Post by cokicd on 2012-02-05
I've followed your advise and reinstalled ubuntu, this time xubuntu 11.10, cause I dislike unity.

Cheers

---

### Post by Cheesemill on 2012-02-05
> **llamabr said:**
> What you did barely worked, and the way you're trying to do it is the long way around.  Your initial installation was specific to your hardware of your laptop.  That's part of what happens during an install.  The software that's running on your desktop is configured for your laptop.  This may even include temperature and fan controls, and other important things you won't see until it melts.

So now you can begin to edit every config file, or you can just do it the right way around the first time, and do a fresh install.  That's what the installation procedure is for.

Maybe for Windows but this simply isn't true for Ubuntu.

Unlike Windows which configures one hardware profile when you first install, Linux probes the hardware and loads the correct drivers each time it boots.

I've successfully moved installations between different PC's several times, the only thing to watch out for is if you are switching graphics card manufacturers it's best to disable the restricted drivers before you make the move. Obviously you cant run a 64 bit installation on 32 bit hardware either.

I have a full installation of Arch on a USB stick and apart from machines which don't USB boot I haven't coma across a single machine it doesn't boot successfully on.

Also if this was true then there would be no way of making a Live CD as this is simply a fully installed version of Ubuntu running from a CD.

---

### Post by searchfgold6789 on 2012-02-06
> **cheesemill said:**
> maybe for windows but this simply isn't true for ubuntu.

Unlike windows which configures one hardware profile when you first install, linux probes the hardware and loads the correct drivers each time it boots.

I've successfully moved installations between different pc's several times, the only thing to watch out for is if you are switching graphics card manufacturers it's best to disable the restricted drivers before you make the move. Obviously you cant run a 64 bit installation on 32 bit hardware either.

I have a full installation of arch on a usb stick and apart from machines which don't usb boot i haven't coma across a single machine it doesn't boot successfully on.

Also if this was true then there would be no way of making a live cd as this is simply a fully installed version of ubuntu running from a cd.+1, most of the drivers are built right into the kernel, which loads every time you boot.

---

