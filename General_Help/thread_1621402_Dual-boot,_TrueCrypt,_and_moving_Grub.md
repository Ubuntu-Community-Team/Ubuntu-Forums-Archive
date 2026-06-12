---
title: "Dual-boot, TrueCrypt, and moving Grub"
date: 2010-11-14
forum: General Help
---

### Post by l1nux1k3 on 2010-11-14
Hello,

I have a dual-boot setup with Windows 7 and Ubuntu 10.10.
I used TrueCrypt to encrypt my drive, but in doing so I lost my Ubuntu boot option (as TrueCrypt boot takes up the MBR).
So now I'm trying again, using TrueCrypt's option of multiple OS installed on same drive. At the moment, it won't let me do that since the Grub boot is on the same partition as the Win7 boot.

In a nutshell, I need to move Grub to another partition so that I can load from that boot option once I <esc> from the TrueCrypt boot.

I created a new partition for Grub, but don't know how to move it.
My partitions as they stand now are:
/dev/sda1 (ntfs system reserved)
/dev/sda2 (ntfs, windows 7)
/dev/sda4 (ext4 -- where I want to move Grub)
/dev/sda 3 (extended, Ubuntu 10.10)
  /dev/sda5 (ext 4)
  /dev/sda6 (linux-swap)

Does anyone know how I can move Grub to sda4?

Or if I'm totally on the wrong track here?

Advice is really appreciated!

Thanks in advance :)

---

### Post by Rubi1200 on 2010-11-14
I am not sure if this will do what you want, but it might be worth taking a look:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

It involves using Method 3: CHROOT

Read the instructions carefully and if you have any questions feel free to ask.

Hope this helps.

---

### Post by l1nux1k3 on 2010-11-16
Thanks Rubi,

For anyone else looking at this thread, I also found what I needed here:


[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by Rubi1200 on 2010-11-16
You are more than welcome :)

Herman's site has numerous great links for dealing with GRUB as well as dual-booting; highly recommended.

---

### Post by alphaamanitin on 2010-11-16
Are you trying to make a hidden OS?  

AlphaA

---

