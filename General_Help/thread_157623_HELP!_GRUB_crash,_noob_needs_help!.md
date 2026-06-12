---
title: "HELP! GRUB crash, noob needs help!"
date: 2006-04-09
forum: General Help
---

### Post by white_tiger_daniel on 2006-04-09
Last night was pretty successful. I set up 2 hard drives, a cd drive and a zip drive. I tried to install fedora core 4 on the 2nd hard drive and boom the installation failed and my bootloader's gone with a big fat Error 15. How can I reinstall it so I can format the 2nd hdd and get back to normal?

---

### Post by ispmarin on 2006-04-09
you can try to 
a) reboot with a ubuntu live cd
b) mount your boot partition with the live cd (using mount /dev/<> /mnt)
c) do a chroot on this partition (chroot /mnt)
d) do a grub-install _from this partition_ (the one you have mounted)
e) pray for all the gods that this works... and grub-install will find all yours other operational systems.

Hope it helps!

---

### Post by louis_nichols on 2006-04-09
Now, I don't really know what error 15 means. Does your GRUB start, but can't find the config file and doesn't load any kernel? Or is it that you don't get any grub at all?

one way to go about this... Boot any CD that gives you a grub shell (or, in case you do get one at startup, use that one). Then at the shell do:

root (hd0)
configfile <path to menu.lst in grub syntax> (this depends a lot on your particular setup, on which partition your working Linux installation is)
setup (hd0)

I haven't done this in quite a while, but I think I remember it correctly. Good Luck! God knows you need it when it comes to grub! :p (personal experience speaking :D )

---

### Post by white_tiger_daniel on 2006-04-11
No my grub doesn't load up but I'm gonna try your solutions now and try and get it working.

---

### Post by greenstar on 2006-04-11
Here is a link to instructions for reinstalling grub. Found them in the wiki.

[Reinstall Grub]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28after%29%7C%28recover%29%7C%28windows%29%7C%28install%29")

Hope this helps.

Greenstar

---

