---
title: "dual boot ubuntu and redhat"
date: 2009-11-06
forum: General Help
---

### Post by sirkanth on 2009-11-06
hey guyz,

                i had redhat on my company desktop .. i installed ubuntu 9.10 on top of it, with the option of having the OS's side by side.. but when i rebooted my comp after installation, i can see only ubuntu in the grub.. cant see the old redhat i had.. need quick help guyz.. or else my company's data is in danger!!!....  plssss help... i am new to ubuntu and redhat ... i need a step by step procedure .. 


thanks in advance

---

### Post by GCoffee on 2009-11-06
Hi sirkanth,

I belive redhat uses a diffrent bootloader to ubuntu. Ubuntu uses GRUB and I think redhat uses LILO. Therfore you would have to do some sort of custom install to have them on the same menu.

If you did not replace your company partition, then your data is perfectly safe, you just need to mount the partition (assuming its a EXT3/4 type.)

You can also try the mount disks widget in the gnome UI. right click on the panel and add widgets. Or whatever it is.. Havent got my ubuntu installed at the moment..

Cheers,
GCoffee.

---

### Post by ManyBeers on 2009-11-06
> **GCoffee said:**
> Hi sirkanth,

I belive redhat uses a diffrent bootloader to ubuntu. Ubuntu uses GRUB and I think redhat uses LILO. Therfore you would have to do some sort of custom install to have them on the same menu.

If you did not replace your company partition, then your data is perfectly safe, you just need to mount the partition (assuming its a EXT3/4 type.)

You can also try the mount disks widget in the gnome UI. right click on the panel and add widgets. Or whatever it is.. Havent got my ubuntu installed at the moment..

Cheers,
GCoffee.

I'm no expert here but Windows uses a completely different bootloader than Grub and it will end up on the Grub boot list without custom install.

In a terminal while in Ubuntu run this command.
sudo fdisk -l
That will list the partition table of your harddrive.

---

### Post by ranch hand on 2009-11-06
Have you run;
```

sudo update-grub

```Grub2 also looks for kernels not just the boot.

Run;
```

sudo sfdisk -l

```Run those and see what happens.

Report back. Post the results of thr last one.

---

