---
title: "Getting GRUB to Boot"
date: 2006-05-18
forum: General Help
---

### Post by Geffers on 2006-05-18
Recently I managed to lose my Ubuntu GRUB boot option; after some advice from this forum I have managed to create a GRUB floppy.

Now at the GRUB prompt I can issue the following;
root (hd0,2)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3
initrd /boot/initrd.img-2.6.12-9-386
boot

This gets my GNOME desktop running, is there any way I can avoid typing in these commands each time I want to boot Ubuntu?

Thanks in advance,

Geffers

---

### Post by groggyboy on 2006-05-18
Once you've booted into Ubuntu, trying typing this in a terminal:> sudo update-grub
See if this puts Ubuntu back into the GRUB menu.

If you want to edit the GRUB menu further, the file is at /boot/grub/menu.lst

Read the examples, and don't be afraid to experiment a bit.  Just make sure you have a backup!

cheers,
groggyboy

---

### Post by dg_w on 2006-05-18
Once in Ubuntu

sudo grub-install /dev/hda

Thats it .... change /hda to wahy ever your root partition is

That will re-instate grub on the boot partition for you ~)

---

### Post by Geffers on 2006-05-18
[QUOTE=groggyboy]Once you've booted into Ubuntu, trying typing this in a terminal:
See if this puts Ubuntu back into the GRUB menu.

If you want to edit the GRUB menu further, the file is at /boot/grub/menu.lst

cheers,
groggyboy[/QUOTE]

My menu.1st appears OK and contains what I recall used to be the menu, it was just getting the menu option to appear I was enquiring about.

Geffers

---

### Post by groggyboy on 2006-05-18
did you try dg_w's suggestion?

you could also try reinstalling GRUB through apt-get/aptitude/synaptic.

---

### Post by dg_w on 2006-05-18
sudo grub-install /dev/hda

Thats it .... change /hda to wahy ever your root partition is

That will re-instate grub on the boot partition for you ~)

---

### Post by Geffers on 2006-05-18
[QUOTE=groggyboy]did you try dg_w's suggestion?

you could also try reinstalling GRUB through apt-get/aptitude/synaptic.[/QUOTE]

Not tried it yet as I'm in Windows at the moment, will do later.

Thanks,

Geffers

---

