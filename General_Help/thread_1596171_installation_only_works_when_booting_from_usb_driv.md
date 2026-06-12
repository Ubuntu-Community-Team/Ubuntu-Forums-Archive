---
title: "installation only works when booting from usb drive?"
date: 2010-10-14
forum: General Help
---

### Post by princeofnam on 2010-10-14
i recently made a startup disk for 10.10 on my external usb drive. i booted up using the usb drive and installed as normal except now when i want to use ubuntu it only works if i select to boot using the same external usb drive.  i made sure to select the laptop's HDD for installing ubuntu, so i'm not sure why this would be.

---

### Post by sgosnell on 2010-10-14
The question is where did you install the bootloader, not where you installed Ubuntu.  You can reinstall grub2 to your HDD by following the tutorial on the forum wiki.

---

### Post by wilee-nilee on 2010-10-14
> **princeofnam said:**
> i recently made a startup disk for 10.10 on my external usb drive. i booted up using the usb drive and installed as normal except now when i want to use ubuntu it only works if i select to boot using the same external usb drive.  i made sure to select the laptop's HDD for installing ubuntu, so i'm not sure why this would be.

I think the second post is probably correct, you might post the bootscript in my signature to confirm what is where. Post it in code tags, hit the # in the reply and put the text in between the generated code tags.

---

### Post by princeofnam on 2010-10-14
how does one choose where the boot loader is installed during the ubuntu installation? i don't recall having the option actually.

how do you post a bootscript?

---

### Post by Quackers on 2010-10-14
File and further details here
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Please use code tags when posting results (New Reply and click on # key)

---

### Post by sgosnell on 2010-10-14
The next-to-last screen has a button labeled "Advanced".  Click that button and the bootloader install location is one of the options.

---

