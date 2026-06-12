---
title: "Dual Boot 32 bit and 64 bit?"
date: 2012-07-27
forum: General Help
---

### Post by Ron O on 2012-07-27
Just installed Ubuntu 12.04 i386 on one partition of HD while keeping Lucid 10.04 as a fall back on another partition, and I am dual booting without issues. But I have bought more RAM (going from 1G to 3G) and would really like to try 12.04 64 bit on the new space I will get when I delete Lucid.

My question is whether it is safe to run a 32 bit and 64 bit OS side by side on seperate partition. Each current installation (both 32 bit) SEES the other partition in Nautilus, even if it is unmounted, and I had some icon files miraculously migrate from one installation to the other.

My 32 bit 12.04 install went well, so I want to keep it until I am sure I can live with 64 bit. There are so many oposing opinions on whether 64 bit is worth the potential problems as a tradeoff for a performance increase most people will not use. So I need to decide for myself.

---

### Post by Cheesemill on 2012-07-27
I've been using 64-bit for years and have never had any problems with it.

If your hardware supports 64-bit then there should be no reason not to use it.

---

### Post by oldos2er on 2012-07-27
> **Ron O said:**
> My 32 bit 12.04 install went well, so I want to keep it until I am sure I can live with 64 bit. There are so many oposing opinions on whether 64 bit is worth the potential problems as a tradeoff for a performance increase most people will not use. 

There's an awful lot of FUD out there about 64-bit; I don't really understand why (people were falling all over themselves to upgrade during the 16- to 32-bit transition, by contrast). Cheesemill said it, if you have 64-bit capable hardware, use 64-bit software.

---

### Post by Ron O on 2012-07-27
But how about the key question- 32 bit side by side with 64 bit?

---

### Post by Cheesemill on 2012-07-27
> **Ron O said:**
> But how about the key question- 32 bit side by side with 64 bit?
Not a problem.

You can even share a /home partition between them if you want, this way all of your settings and user files will stay synced between the two.

---

### Post by LiamOS on 2012-07-27
As long as you're not planning on doing anything mad(chrooting from one to the other, sharing kernels, etc.), running a x86 and a x86_64 system side by side is perfectly fine.

---

### Post by oldos2er on 2012-07-27
> **Ron O said:**
> But how about the key question- 32 bit side by side with 64 bit?

It's called multiarch. [https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)

---

### Post by efflandt on 2012-07-27
Operating systems on different partitions run independently, so it does not matter at all as long as you are not chrooting to different bits.  There is no problem reading or writing data files on other drives.

At one time I was booting 32-bit WinXP Home, 64-bit WinXP Pro beta, and 64-bit SuSE all on the same drive.  And once I discovered Ubuntu a week before Ubuntu 9.10 was released, changed that to 32-bit WinXP Home, and both 32-bit and 64-bit Ubuntu to compare them.

I currently have a 2 GB tablet PC that runs 32-bit Win7 Pro from its 32 GB SSD, and both 64-bit Lubuntu and Ubuntu 12.04 sharing a common /home on 32 GB SDHC (to compare those).

My desktop runs 64-bit everything due to 8 GB RAM.

---

### Post by Ron O on 2012-07-28
Thanks all. Just the info I was looking for.

---

