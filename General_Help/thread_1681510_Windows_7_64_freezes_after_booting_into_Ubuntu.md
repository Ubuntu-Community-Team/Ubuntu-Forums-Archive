---
title: "Windows 7 64 freezes after booting into Ubuntu"
date: 2011-02-04
forum: General Help
---

### Post by einekleinepinguin on 2011-02-04
I apologize in advance if I've posted in the wrong section (or if someone else has posted this before and I missed it). I bought an Asus N61jq a few months ago, and almost every time I boot into Ubuntu (live usb, and wubi install) and reboot into Windows 7 x64, the machine starts freezing; no BSODs no nothing, just locks up. This freezing is seemingly random, and can happen even after 3-4 reboots. I realized this has something to do with me mounting my ntfs partitions in Ubuntu, and the problem disappeared after running scandisk.

The thing is, I've never had problems with mounting ntfs partitions in linux, what do you guys reckon the problem is?

---

### Post by Mark Phelps on 2011-02-04
> **einekleinepinguin said:**
> The thing is, I've never had problems with mounting ntfs partitions in linux, what do you guys reckon the problem is?

You answered it yourself -- you're mounting your Win7 OS partition in Linux -- which is a bad idea.

If you're interested is in sharing files between the two OSs, a better solution is to migrate them all to a shared NTFS data partition.

As long as you keep mounting your Win7 OS partition in Ubuntu, you're risking running into these problems.

---

### Post by drewsus on 2011-02-04
> **Mark Phelps said:**
> You answered it yourself -- you're mounting your Win7 OS partition in Linux -- which is a bad idea.

If you're interested is in sharing files between the two OSs, a better solution is to migrate them all to a shared NTFS data partition.

As long as you keep mounting your Win7 OS partition in Ubuntu, you're risking running into these problems.

Ive been dual booting for years (tri booting with OS X now too - hfsplus) and mounting the winxp,vista,7 partition and rw'ing it has never once been a problem.

---

### Post by einekleinepinguin on 2011-02-04
> **drewsus said:**
> Ive been dual booting for years (tri booting with OS X now too - hfsplus) and mounting the winxp,vista,7 partition and rw'ing it has never once been a problem.

Exactly, I mean, I've had windows moan and gripe and tell me to run scandisk (excuse the antiquated nomenclature) , but I've never had any "real" problems. I'm wondering if this has to do with the x64 version of windows, seeing as how this is the first time I've used a 64-bit os and I've never had any problems with 32 bit windows editions and ntfs partitions.

I could always mount ntfs partitions in read-only mode, but not being able to write to them is kind of a hassle.

---

### Post by drewsus on 2011-02-04
> **einekleinepinguin said:**
> Exactly, I mean, I've had windows moan and gripe and tell me to run scandisk (excuse the antiquated nomenclature) , but I've never had any "real" problems. I'm wondering if this has to do with the x64 version of windows, seeing as how this is the first time I've used a 64-bit os and I've never had any problems with 32 bit windows editions and ntfs partitions.

I could always mount ntfs partitions in read-only mode, but not being able to write to them is kind of a hassle.

I dont know, I have to suspect it is something else. I have built two new computers recently for two different friends that both had 64 bit Win7 and Ubuntu 10.10 dualboot. Neither had to do anything out of the ordinary on Win boot. My computer is Win7 32bit, though.

---

