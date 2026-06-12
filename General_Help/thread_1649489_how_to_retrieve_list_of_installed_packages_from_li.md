---
title: "how to retrieve list of installed packages from live cd."
date: 2010-12-20
forum: General Help
---

### Post by rcayea on 2010-12-20
Hey Everyone,

I am having to reinstall ubuntu because of my silly mistake. Anyway, my questions is, when booting from live cd, how would I get the terminal to print out what I have listed on my actual hard drive? I know this works if I am logged into my actual Ubuntu hard drive, but I can't do that: dpkg --get-selections > installed-software. 

I am trying to get a list of installed packages because I can't actually boot into my current ubuntu hard drive. 

Thanks,
Randy

---

### Post by clrg on 2010-12-20
Assuming your filesystems aren't corrupted, you can:

1. Boot live cd
2. Mount your partitions
2.1 Use fdisk -l to see what they're called
2.2 Mount the filesystems, for example "mount /dev/sda1 /mnt" and "mount /dev/sda2 /mnt/home"
2.3 Mount dev and proc, "mount -o bind /dev /mnt/dev" and "mount -t proc /proc /mnt/proc"
3. Chroot into your hard drive: "chroot /mnt /bin/bash"
4. You are now in your old environment. You can now make a list of all installed packages.
5. Type exit to exit chroot.
6. Copy the list from wherever you created it to a safe place, for example, and usb stick.
7. Umount all mounted partitions, like /mnt/boot /mnt/dev /mnt/proc /mnt/home etc.
8. Reboot and thank me =D

---

### Post by rcayea on 2010-12-20
Thank you very much! I will give this a go and marked as solved if successful.

---

