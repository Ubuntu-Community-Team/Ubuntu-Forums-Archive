---
title: "Dual-Boot Woes / Booting Errors Ubuntu 9.10"
date: 2010-02-07
forum: General Help
---

### Post by brokenrhythms on 2010-02-07
Hello-

I would greatly appreciate some help on my current issue.

I was currently running ubuntu 9.10 on my laptop.

I set aside a partition of 70 gigs to install Windows Vista as dualboot.

For some reason I had an error installing Vista, it would stop at the final "Completing Installation" portion and not advance.

After temporarily giving up on the Vista installation, i decided to wipe out this 70 gig partition using GParted and just load ubuntu again.

Now i get the message "No Bootable Device" and I can't even boot Ubuntu.

Any ideas??

---

### Post by OrangeCrate on 2010-02-07
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by ajgreeny on 2010-02-07
You will probably need to reinstall grub as windows will have taken over the MBR again, even though the installation was not successful.

How to restore the Ubuntu grub bootloader (9.10 and beyond)

Ubuntu 9.10 uses Grub 2, so you need to find out what your drives are using live CD:
    sudo fdisk -l
From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
Still in the terminal, type:
    sudo mkdir /media/sda5
    sudo mount /dev/sda5 /media/sda5
To reinstall grub:
    sudo grub-install --root-directory=/media/sda5 /dev/sda
Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

Good luck.

---

