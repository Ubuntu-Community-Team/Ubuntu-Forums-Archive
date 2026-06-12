---
title: "Problem with triple boot w7/8 and ubuntu"
date: 2012-03-25
forum: General Help
---

### Post by Archy108 on 2012-03-25
Hello everybody!

I have w7 and 8,so I installed ubuntu on my D hdrive(so ubuntu is neboring with w7). But on my second system loading after install ubuntu didn't appear in OS booting list(only w7 and 8). How can i fix that?

sorry for my enlish - I'm from Russia =)

---

### Post by Sylslay on 2012-03-25
If ubuntu boot up ok,

try comand in terminal:

sudo os-prober
sudo update-grub

Witch part of HHD is grub installed?

---

### Post by oldfred on 2012-03-25
Post link to run of boot info script from this. It may also fix you issue.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

To understand Windows multibooting with BIOS and MBR. Not new UEFI.

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you want two entries in grub you may have to repair your second windows install if it is a primary partition. Otherwise both Windows will be one entry in grub and then Windows will ofter the two choices of Windows versions.
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

