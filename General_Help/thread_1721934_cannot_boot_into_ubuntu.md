---
title: "cannot boot into ubuntu"
date: 2011-04-05
forum: General Help
---

### Post by elgobuda on 2011-04-05
Ok, I have two problems

I have downloaded Ubuntu Netbook and created a USB drive and a CD with the image. When I plug in the USB into Toshiba NB250 netbook it just doesn't boot. I've changed the boot order in BIOS, I've tried f12 to get to boot menu and select the USB drive. I've also tried a CDROM drive too, both with an altered boot order and from boot menu. No matter what I use, Windows 7 loads. I don't even get a screen to suggest that the USB drive is being read. 

The USB drive is fine, I have used it two weeks ago to install Windows 7 on the same netbook.

I also have a Sony VGN NR32 L. Here, it gets to a screen giving me a choice of trying Ubuntu or installing it. No matter what choice I make, the laptop restarts and boots to that same screen giving me a choice of what to do.

What shall I do?

---

### Post by Bucky Ball on 2011-04-05
How did you make the USB installer?

---

### Post by elgobuda on 2011-04-05
I used the suggested program **Universal USB Installer**.

---

### Post by elgobuda on 2011-04-05
Any help?

---

### Post by Rubi1200 on 2011-04-05
Which version are you trying to use?

I recommend UNetbootin for USB sticks:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by elgobuda on 2011-04-05
Version of Ubuntu or USB installer? Latest for both...

Will try what you have suggested

---

### Post by elgobuda on 2011-04-05
that didn't work. still refuses to boot into ubuntu.

---

### Post by Rubi1200 on 2011-04-05
Sorry, I meant which version of Ubuntu.

If by the latest you mean 11.04, it is still in beta and problems are to be expected.

---

### Post by IHeequ5i on 2011-04-05
I don't think the version of Ubuntu is going to make a difference. This sounds like the laptop is refusing to recognize any other boot device other than its primary hard drive.

You can try poking around on Toshiba's website and see if they have an updated BIOS for your laptop.

---

### Post by Rubi1200 on 2011-04-05
> **Doomspark said:**
> I don't think the version of Ubuntu is going to make a difference. This sounds like the laptop is refusing to recognize any other boot device other than its primary hard drive.

You can try poking around on Toshiba's website and see if they have an updated BIOS for your laptop.
Possibly, except the OP is having problems on a Sony as well (presumably with the same image file).

Could be a corrupted image?

Check the integrity and then try either another USB or burning to CD at the slowest possible speed.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Bucky Ball on 2011-04-06
Try to torrent the ISO from the alternative downloads. It is the most reliable way. Try 10.04 LTS. It is stable and you can expect less probs (not that the release is definitely the cause; let's just start at the beginning and rule that out). Make boot dongle with UNetbootin. Seems to be the one most successful.

Toshibas can be problematic. I have one.

---

