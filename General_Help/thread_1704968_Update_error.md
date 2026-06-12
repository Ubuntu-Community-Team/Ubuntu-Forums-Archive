---
title: "Update error"
date: 2011-03-11
forum: General Help
---

### Post by 176-671 on 2011-03-11
Hi, I got a problem with the update. Somewhat I think my system (Ubuntu 10.10)  was interrupted by power outage or something. 

It told me I could run a partial upgrade, and I did so. Which caused an eternal loop in terminal that looked like this:
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

These lines went on and on for hours until I shut it down.

The next time I tried the update I get a message that tells me to run  «sudo aptitude -f install». When I do so I get this error: sudo: aptitude: command not found.

I found somewhere I could try "locate aptitude".
And got this path: /etc/bash_completion.d/aptitude
So I tried the command with the whole path: 
sudo /etc/bash_completion.d/aptitude -f install
sudo: /etc/bash_completion.d/aptitude: command not found

I went ahead to Synaptic instead, and then I'm told to run this command:
sudo dpkg --configure -a
Doing so causes the same eternal loop as I had first.

How do I fix this?

---

### Post by plucky on 2011-03-11
Maverick does not have aptitude installed by default.

Try ```
sudo apt-get install -f
``` instead.
This will attempt to fix any broken packages.

Good Luck

---

