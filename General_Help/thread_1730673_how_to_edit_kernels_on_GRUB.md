---
title: "how to edit kernels on GRUB"
date: 2011-04-16
forum: General Help
---

### Post by javajames97 on 2011-04-16
I have GRUB to allow me to boot windows and Ubuntu, i recently noticed that my list of kernels is getting clogged up with all the updates. So i went online to try and find out how to get rid of the unwanted partitions and also how to add new ones - i am going to attempt to hackintosh, and will need to know how to add kernels. What i found out was; the boot menu in GRUB had a file that is supposed to be called 'menu.lst' (Lst not ist), and that all i needed to do was edit this, that it wouldn't delete the kernels, but that i don't need to, i only need to add and remove links to kernels on the GRUB menu. The problem is that after looking, i don't have that menu.lst file, i have a file containing the image files for 'memtest', but not for my GRUB. I am using 10.04, i don't know what version of GRUB im using but i'm using whichever one comes with 10.04. Could someone please point me in the direction of the files i need to edit or what i need to do to add and remove kernels? *if you point me in the direction of the menu file i can probably go from there. thanks in advance

---

### Post by TeoBigusGeekus on 2011-04-16
Since Karmic (I think), ubuntu uses grub2. The menu.lst file was in use in the older grub version (grub legacy).

To add new kernels, simply run
```
sudo update-grub
```
in terminal and grub will detect any new kernels present on your pc.

To remove older ubuntu kernels, open synaptic package manager and search for linux-image.
Keep the 2 newest ones, right-click>completely remove the rest.
Run 
```
sudo update-grub
```
to update your grub (who'd have thought) and you're done.

For more info about grub2:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by javajames97 on 2011-04-16
> **TeoBigusGeekus said:**
> Since Karmic (I think), ubuntu uses grub2. The menu.lst file was in use in the older grub version (grub legacy).

To add new kernels, simply run
```
sudo update-grub
```
in terminal and grub will detect any new kernels present on your pc.


when you say, this does it detect just any kernels, or does it have to be the ones on a certain partition (what about unix or windows kernels?). Am i removing the ones highlighted in green? (i.e. first green 'generic' keep, second green 'generic' remove, and where are the recovery options (are that included with each, because i want to be careful i don't only keep the generic and recovery)).

---

### Post by TeoBigusGeekus on 2011-04-16
It should detect both windows' and other linux bootloaders.

The fallback kernels go together with the normal ones.
Just purge all the old ones, keeping just the 2 newest ones, update grub and you should be fine.

---

