---
title: "Hard Drive Crashed and Home Directory Encrypted!!"
date: 2012-02-12
forum: General Help
---

### Post by mojo_man on 2012-02-12
Hi,

My Grub/system really messed up and despite attempts to repair it, it won't boot. I decided to use a Ubuntu 9.10 boot CD to get the stuff from my home directory and do a reinstall. Guess what? The home directory is encrypted.
I found instructions on how to decrypt it but the problem is that I never created a separate parition for my /home directory. Every is in /dev/sda1
So when I mount /dev/sda1 I can get access to /home/user

It seems that I have to be to mount "home/user" on my hard drive to exactly the same /home/user on the boot CD. And then create a user with the same name and execute some encryptfs command.

Can someone tell me how I can go about this given my circumstances. Can I just CP the directory contents to /home/user after mounting from /dev/sda1?
I am confuzed.

---

