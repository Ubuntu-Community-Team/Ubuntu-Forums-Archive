---
title: "UnetBootin"
date: 2012-01-22
forum: General Help
---

### Post by woopud on 2012-01-22
I'm using Ubuntu 11.11 and I'm trying to make a bootable usb drive with Toorox linux on it, downloaded and checksummed the iso and is fine.  When using unetbootin it starts creating the disk and sfter 5 seconds it says it's done but I know that's impossible.

---

### Post by shymega on 2012-01-22
Hi,

Have you tried booting off the USB Drive?

Can you try that and report back?

--
sm

---

### Post by woopud on 2012-01-22
Yes, when I boot off the usb I get the Blue unetbootin screen whit the only option being "default" and then it counts down the 10 seconds and start back at 10 seconds again.  I know it should take much longer to copy a 1,4 GB iso to the usb drive.

Bert

---

### Post by abhijeet.1308 on 2012-01-22
i think you should try making other os as bootable using UnetBootin

if this also having same probleam i suggest you you should try reinstalling fresh copy of UnetBootin

-savio

---

### Post by WasMeHere on 2012-01-22
Hi Bert,

Have you used the same version of Unetbootin to make another boot drive, for example the one you used to install Ubuntu?

If that is the case, I think that Unetbootin cannot make a boot drive from the Toorox iso file. Maybe ***another USB boot drive creator*** would solve your problem. Or you could burn a DVD and ***boot from a DVD drive***. If there is no built-in one, you can use an external DVD drive attached via USB (maybe borrow one, or attach an internal box temporarily via an adapter).

Or simply ***select another linux distro***, that is easier to make bootable via USB. There are many interesting distros available.

Have fun finding out :-)
Olle

---

### Post by shymega on 2012-01-22
In the Ubuntu Administration Menu, open the Startup Disk Creator. Use your ISO as the source and your USB Disk as the destination.

Then Click 'Make Startup Disk'

Good Luck.

--
sm

---

### Post by woopud on 2012-01-22
I tried two other linux iso files which worked fine with unetbootin so I'm not sure why the toorox.iso won't work.  Also tried Startup Disk Creator but it just tells me "installation failed".  How do I remove the selected iso in the source disc image window to try another iso?  If I close the program and reopen it the previous selected iso is still there.

Bert

---

### Post by WasMeHere on 2012-01-22
> **woopud said:**
> I tried two other linux iso files which worked fine with unetbootin so I'm not sure why the toorox.iso won't work.  Also tried Startup Disk Creator but it just tells me "installation failed".  How do I remove the selected iso in the source disc image window to try another iso?  If I close the program and reopen it the previous selected iso is still there.

Bert
Simply select another source iso file. At least it works for me. Otherwise I think there is something wrong with your Unetbootin, and you should reinstall it.

But probably you need some other tool for Toorox.

---

