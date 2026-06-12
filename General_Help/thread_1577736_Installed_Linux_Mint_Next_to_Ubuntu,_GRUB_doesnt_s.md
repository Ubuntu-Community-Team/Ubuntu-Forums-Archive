---
title: "Installed Linux Mint Next to Ubuntu, GRUB doesnt show list"
date: 2010-09-19
forum: General Help
---

### Post by lamb123 on 2010-09-19
Hey,

I divided my 250GB HDD into 2 pieces, created a new primary partition (sda3, ext4), installed Mint to that partition but I didnt choose to install GRUB during install.

How to get GRUB to show mint?

Also, when I already have 1 linux distro installed and want to install another, I dont have to change anything for SWAP parition right? All distros use the same and know where to look for it?

Thanks.

---

### Post by mrinehart93 on 2010-09-19
I think to add Mint to GRUB, you'll need to do a "sudo update-grub"... I'm not 100% sure though. If anything, it just won't work. But I think you are right about the SWAP thing. Mint and Ubuntu should be able to use the same SWAP.

---

### Post by Rubi1200 on 2010-09-19
Run```
 sudo update-grub
``` in the terminal as suggested above. This should pick up Mint and add it to the GRUB menu.

Which version of Mint are we talking about?

---

### Post by lamb123 on 2010-09-19
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint Debian Edition (1) on /dev/sda3
done


seems to have worked

thanks

---

### Post by Rubi1200 on 2010-09-19
You are more than welcome :)

Just be aware that Mint Debian Edition *may* not have utilized the existing swap partition, but as long as you have enough RAM it probably won't be an issue.

Please mark this thread Solved using the Forum Tools near the top of the page.

---

### Post by lamb123 on 2010-09-19
> **Rubi1200 said:**
> 
Just be aware that Mint Debian Edition *may* not have utilized the existing swap partition, but as long as you have enough RAM it probably won't be an issue.


yup, typing ```
free
``` into terminal shows SWAP usage 0 out of 0.

---

### Post by Rubi1200 on 2010-09-19
> **lamb123 said:**
> yup, typing ```
free
``` into terminal shows SWAP usage 0 out of 0.
Ok, I cannot be sure of this, but I wonder if this is because this is a new version for the developers? The other Mint versions picked up and added any existing swap partition.

---

### Post by Rubi1200 on 2010-09-19
> **lamb123 said:**
> yup, typing ```
free
``` into terminal shows SWAP usage 0 out of 0.
I think I have found the solution:

If you check fstab on Ubuntu and Mint Debian you should see that the entry for swap probably has the wrong UUID.

Copy the UUID from Ubuntu (which you know to be correct) and go to Mint.

Open a terminal and ```
sudo gedit /etc/fstab
```Enter the correct UUID in the entry > swap was on /dev/sdx (whatever is relevant in your case) then save and reboot.

You should then find that swap is activated if you run the command ```
free
```Hope this helps.

---

