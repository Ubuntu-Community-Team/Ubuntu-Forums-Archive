---
title: "update killed x"
date: 2011-01-24
forum: General Help
---

### Post by superalanliu on 2011-01-24
I hadn't updated until yesturday night, today after the massive update and reboot, my x stopped working.

What happens is, after the splash screen, both screens goes black and unresponsive. Tried killing X and alt + ctrl + f1 etc. I can probably fix this myself if I could access the terminal but, the other day I had to be stylish and remove everything from my grub boot besides Windows 7 and the default Ubuntu so I can't boot into root terminal.

So, how would I gain access to a console before X starts? Any idea of fixing this?

Thanks in advance!

---

### Post by matt_symes on 2011-01-24
Hi

Boot into a LiveCD and chroot.

Kind regards

---

### Post by Krytarik on 2011-01-24
Or just edit the kernel boot parameters upon boot and replace "quiet splash" with "single".

---

### Post by superalanliu on 2011-01-25
quiet splash -> single worked like a charm! Thanks!

Just FYI - I had to reinstall my ATI driver to get X to work.

---

### Post by Krytarik on 2011-01-25
Just for my information, how did you install the driver in the first place, manually with the installer from AMD's website; or via "Hardware Drivers" (10.04) / "Additional Drivers" (10.10) or with a package manager?

---

### Post by superalanliu on 2011-01-25
Manually from AMD's website.

I downloaded the driver using my Windows 7. Mounted the HD in Ubuntu and ran it from there.

---

### Post by Krytarik on 2011-01-25
If you install the driver manually like this, you have to repeat it each time when the kernel gets updated. If you install it as a package, you don't have to.

---

### Post by superalanliu on 2011-01-25
> **Krytarik said:**
> If you install the driver manually like this, you have to repeat it each time when the kernel gets updated. If you install it as a package, you don't have to.

Whoa, did not know that. You're too awesome. I'll be sure to install it as a package.

---

### Post by Krytarik on 2011-01-26
But try to remove the manually installed driver somehow before, look into the install instructions therefore. May be not really possible though.

---

