---
title: "Grub error 15: File not found"
date: 2011-03-26
forum: General Help
---

### Post by linuxn3wbie on 2011-03-26
Hi everyone

I did search this forum and the entire Internet for this error and tried all solutions I found so far, but nothing helped yet. I bought a brandnew PC with a pre-installed Windows installation on it, and of course I formatted it immediately (who wants Windows?). I then installed Puppy Linux, which used to be my favourite operating system.

However, I saw that it would no longer be a good idea to use Puppy Linux anymore. My PC has 5 GB of RAM and only 3 of it was getting used. This is why I tried to give Ubuntu 64-bit a shot. I booted from the Ubuntu CD, and I partitioned my drive as such:

sda1 - 10 GB: swap
sda2 - 140 GB: plenty of space for ubuntu
sda3 - 850 GB: storage

I entered '/' (minus the 's) as the mount point for sda2 as this'll contain the Ubuntu installation. I entered '/home' as the mount point for sda3. I then choosed to install the bootloader to sda2.

Everything went fine, the installer gave no error whatsoever and at the end it tells me to withdraw the disk and restart. Upon restart, GRUB comes up with a Grub error 15: File not found.

This has been giving me a headache for days. The farthest I've gotten is that I fixed the problem, but messed it up even more. I'd then get error number 8, and a message that sounded something like: 'The kernel should boot first', but I don't need advice on how to fix this seeing as I got error 15 again (reinstalled for the ninth time)

Anyone capable of helping me booting Ubuntu is a hero! I saw and heard lots of good things about it and I can't wait to try it out, but so far I didn't have a good experience with Ubuntu. :(

---

### Post by vivek.pandey on 2011-03-26
if you are a newbie to ubuntu installation why dont you just ubuntu to install itself on its own . i mean dont do manual settings . let it do automatically. when i installed 5 months back . i just let ubuntu what it wanted

---

### Post by linuxn3wbie on 2011-03-26
No. The reason I want to manually partition is that I ALWAYS keep the operating system and the data separated. That way I can mess with operating systems as much as I want without having to care about all my personal files.

On a side note, the problem has been solved. I don't know how it got solved. I just tried the install again and now it just worked. It's now downloading tons of updates, I see. :D

---

