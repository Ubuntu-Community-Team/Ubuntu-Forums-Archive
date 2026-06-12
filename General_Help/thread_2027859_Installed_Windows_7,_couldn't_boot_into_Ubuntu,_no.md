---
title: "Installed Windows 7, couldn't boot into Ubuntu, now can't boot into Windows"
date: 2012-07-17
forum: General Help
---

### Post by Hungry Man on 2012-07-17
So I Couldn't boot into Ubuntu after installing Windows 7.

I fixed that by doing the following:

1) Boot into LiveCD

2) Open up root terminal

3) mkdir /mnt/tmp

4) mount /dev/sda1 /mnt/tmp

5) grub-install --root-directory=/mnt/tmp /dev/sda

Now I can't boot into windows lol

edit: I assume I have to chainload into the Windows 7 bootloader.
edit2: Nevermind - solved or whatever. I just had to run update-grub lol

---

