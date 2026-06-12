---
title: "Couple of issues !!  (boot up, mad cursor and wireless)"
date: 2009-11-15
forum: General Help
---

### Post by Tom_T on 2009-11-15
Upgraded from 9.04 -> 9.10...  went smoothly.

But I have a couple of none critical issues.
Acer Aspire 1694 WMLI

1. When typing the cursor often jumps across the screen. meaning I end up typing over what I've already typed.

2. ubuntu seems much slower booting up.
I get grub, followed by the black screen with boot and uuid details, then the white ubuntu logo and finally the fancy ubuntu loader with the animated graphics.

After that I get the login screen.. All this takes a lot longer than the loader in 9.04.

3. My wireless seems to keep pausing. I can ping network devices, but not the wireless router :(  after a couple of seconds all is well again..

Any ideas ??  Many Thanks

---

### Post by fluffman86 on 2009-11-15
1: Go to System > Preferences > Mouse, and there should be an option to disable tap-to-click.  There is also an option that will allow a smart sensor to see if your palm or your finger is tapping.  That one doesn't work so well for me, so I just disabled tap-to-click.

2: Which part of the boot is slowing down?  If it's the part where you're just waiting for grub to start, I had the same problem.  Turns out that part of grub was on the MBR, and part was in my /boot directory.  Both were on different Hard Drives.  Anyway, I doubt that's the problem with a laptop, but still open up your BIOS and check your boot settings.  There's usually no need to have CD or USB devices try to boot before your primary HDD.

3: Check System > Administration > Hardware to see if there is a proprietary driver for your Wireless card.

---

### Post by Tom_T on 2009-11-15
Thanks.

1. Disabled touchpad whilst typing... I'll see if this works for me :)

2. From power on to grub is about the same as before.
It's the time from selecting ubuntu to login and then to desktop.

3. There are NO proprietary drivers.
lspci shows:
```
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

Thanks :)

---

### Post by ctult on 2009-11-15
You may want to download a proprietary driver. I had the same problem.

---

### Post by Tom_T on 2009-11-15
Thanks..  can you point me in the right direction ?

---

