---
title: "make a .iso"
date: 2009-12-23
forum: General Help
---

### Post by ubudog on 2009-12-23
How do I make a .iso?

---

### Post by Zerorebels on 2009-12-23
not sure you could always google ISO Maker. or something ill check and get back to you on that one.

---

### Post by Zerorebels on 2009-12-23
[http://www.magiciso.com/tutorials/miso-makebootablecd.htm](http://www.magiciso.com/tutorials/miso-makebootablecd.htm) here you go. full tutorial.

---

### Post by HeadHunter00 on 2009-12-23
use acetoneiso.

---

### Post by Treeh on 2009-12-23
> **Zerorebels said:**
> [http://www.magiciso.com/tutorials/miso-makebootablecd.htm](http://www.magiciso.com/tutorials/miso-makebootablecd.htm) here you go. full tutorial.

This is for Windows...using proprietary software. Also, there is no need to make two posts.

I presume the OP wants to create a .iso from a CD/DVD (or from a hard drive). You can simply use Terminal:
[http://kevin.vanzonneveld.net/techblog/article/make_iso_images_on_linux/](http://kevin.vanzonneveld.net/techblog/article/make_iso_images_on_linux/)

---

### Post by Zerorebels on 2009-12-23
actually as far as i know MagicISO is for both windows/Linux and macs.

---

### Post by Treeh on 2009-12-23
> **Zerorebels said:**
> actually as far as i know MagicISO is for both windows/Linux and macs.

What...

No, it simply isn't. Go to "Download" and you'll see the list of supported operating systems. Notice how every single entry has "Windows" in it...and how *it costs money*.

---

### Post by ivicks on 2009-12-23
dd if=/? of=/filename.iso

example of backing up data from a hd and saving the output to an iso file.

dd if=/dev/sdb1 of=/backup/filename.iso

To Mount an ISO

mount -o loop /backup/filename.iso /mnt/mountfolder

---

### Post by orlox on 2009-12-23
@ubudog

please clarify what the source of your ISO is. Do you want an ISO done with local files in your hard-drive?? Or you want to copy a disc into an ISO image?

---

### Post by HermanAB on 2009-12-23
man mkisofs

---

### Post by ubudog on 2009-12-25
> **Treeh said:**
> This is for Windows...using proprietary software. Also, there is no need to make two posts.

I presume the OP wants to create a .iso from a CD/DVD (or from a hard drive). You can simply use Terminal:
[http://kevin.vanzonneveld.net/techblog/article/make_iso_images_on_linux/](http://kevin.vanzonneveld.net/techblog/article/make_iso_images_on_linux/)

Thank you.

---

