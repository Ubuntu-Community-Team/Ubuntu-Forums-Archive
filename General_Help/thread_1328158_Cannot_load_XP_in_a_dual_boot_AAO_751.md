---
title: "Cannot load XP in a dual boot AAO 751"
date: 2009-11-16
forum: General Help
---

### Post by Udibuntu on 2009-11-16
Hi All,

I just installed 9.10 on my new AAO 751 (poor performance, many issues) and am trying to load XP again - no dice.

Even though I see XP as an option and choose it, Ubuntu loads instead.

Please help!

---

### Post by blazemore on 2009-11-16
Okay, from ubuntu would you please open a terminal and type the following instruction, then press enter:
```
sudo update-grub
```

Tpe your password, then press Enter.

Can you please copy and paste the terminal's respone in this thread, then reboot and see if it works. if it doesn't I should be able to help you further.

---

### Post by realzippy on 2009-11-16
should it not be:

**sudo update-grub2**

on Karmic?

---

### Post by blazemore on 2009-11-16
Yes and no. On karmic, update-grub actually runs the command update-grub2. it's that way in order to fit in with all the old documentation I think.
I installed with Alternate CD in expert mode: it lets you use normal grub!

---

### Post by Udibuntu on 2009-11-16
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
done


Thanks Blaze, it worked at least once. I'll mark it solved and move on to try and improve the extremely low performance issues.

Udi

---

### Post by blazemore on 2009-11-16
I've got an Aspire One. I found installing the kernel from [www.kuki.me](www.kuki.me) helped a lot, as did disabling journaling on the filesystem (if you're using ext3 or ext4)

If you want to install the kernel do this
```
wget http://www.kuki.me/downloads/PT%20KUKI%20ME%20KERNEL%20HEADERS%20LINXISP
wget http://www.kuki.me/downloads/PT%20KUKI%20ME%20KERNEL%20LINXISP
sudo dpkg -i *kuki*deb

```

If you want to disable journaling, boot from a Karmic LiveCD (Or LiveUSB in your case), then run the following command (assuming your root partition is /dev/sda1)

```
sudo tune2fs -O ^has_journal /dev/sda1
```

Then reboot

As always, back up first.

---

