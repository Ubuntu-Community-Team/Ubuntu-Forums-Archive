---
title: "How do I keep dual systems separate?"
date: 2010-01-24
forum: General Help
---

### Post by munchkinmunchkin on 2010-01-24
I have 9.10 karmic working fine on my main internal hard disk, and decided to install Linux Mint on an external USB hard disk, that shouldn't cause any problems I thought, wrong!

Upon shutting down and removing the USB drive and rebooting I was confronted with a "Grub rescue>" prompt.

I re-plugged in the USB Linux Mint drive and rebooted and 9.10 Karmic was in the Linux Mint boot menu.

It seems the installation of Linux Mint on an external USB hard drive modified the Grub on my original internal hard disk?

After some panic searching I found that this restored my Grub to working again.

>    1. Boot from the CD/USB flash drive from which you installed Ubuntu
   2. Open terminal (It is there under Accessories)
   3. type in sudo fdisk -l
   4. then type sudo mount /dev/sdAB /mnt , where A is your drive and B is your linux partition. In my case, I typed in sudo mount /dev/sda7 /mnt
   5. install GRUB again by typing this sudo grub-install --root-directory=/mnt /dev/sdA , where A is your drive. In my case, I typed sda
   6. Now type sudo umount /mnt


Not sure if the above was correct but 9.10 Karmic seems to work fine?

Booting from the Linux Mint USB drive now brings up the 9.10 Karmic login with no option to select Mint.

So the question, how can I keep different systems completely separate on their own hard drives so that I can select them from the computer's boot menu (F12) upon startup?

I don't want the installation on an external or other internal drive interfering with the contents of another drive. I want them as independent systems.

Would disconnecting the internal drive before installing Linux Mint to the external USB drive fix the problem?

---

### Post by Jackzor on 2010-01-24
> **munchkinmunchkin said:**
> I have 9.10 karmic working fine on my main internal hard disk, and decided to install Linux Mint on an external USB hard disk, that shouldn't cause any problems I thought, wrong!

Upon shutting down and removing the USB drive and rebooting I was confronted with a "Grub rescue>" prompt.

I re-plugged in the USB Linux Mint drive and rebooted and 9.10 Karmic was in the Linux Mint boot menu.

It seems the installation of Linux Mint on an external USB hard drive modified the Grub on my original internal hard disk?

After some panic searching I found that this restored my Grub to working again.



Not sure if the above was correct but 9.10 Karmic seems to work fine?

Booting from the Linux Mint USB drive now brings up the 9.10 Karmic login with no option to select Mint.

So the question, how can I keep different systems completely separate on their own hard drives so that I can select them from the computer's boot menu (F12) upon startup?

I don't want the installation on an external or other internal drive interfering with the contents of another drive. I want them as independent systems.

Would disconnecting the internal drive before installing Linux Mint to the external USB drive fix the problem?

First thing that comes to my mind is boot to Karmic then pull the usb out then install grub and restart without the usb stick in. Hopefully that will be fine.

---

### Post by garvinrick4 on 2010-01-24
Do they have 2 different grubs 9.10 is grub2 what is Mint?  Look into it then google for
that fix. I do not know what grub mint has so cannot tell you with info I have.

---

### Post by hemimaniac on 2010-01-24
If you are using mint 7, it is still the "legacy grub" if you went with mint 8 it is built on 9.10 so it will have grub2 as default. Not alot of help, i know. but hopefully narrows down the search.

---

### Post by Ginsu543 on 2010-01-24
When you installed Linux Mint, did you tell it to install grub to the partition (i.e., your external hard drive) you were installing it to? The reason I ask is that (at least for Ubuntu) the default setting for installing the grub is (hd0), which is your main hard drive. There is a button on the last page before you click "Install" called "Advanced...", which, if you click on it, will give you the option of changing the location where the installer will install grub.

---

