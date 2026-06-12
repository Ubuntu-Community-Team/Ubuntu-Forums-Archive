---
title: "/home on fat partition"
date: 2009-08-10
forum: General Help
---

### Post by nikhilbhardwaj on 2009-08-10
i was just curious
is ti possible to mount your /home on a fat partition
maybe not during the installation but afterwards by editing the fstab
can it be dangerous

please enlighten me

---

### Post by mcduck on 2009-08-10
No, it's not possible. FAT and NTFS filesystems aren't able to handle file ownerships and permissions as they are used in Linux/Unix systems. And there are some files in user's home directories that require certain ownership and permissions for your system to work correctly.

There are some Linux distributions that have hacked their way around this problem, but it's definitely not something that would be easy to implement on any normal distribution, and it really only makes sense in some special situations. 

If you want to do this to make sharing files between Linux and Windows easier on a dual-boot system you could instead just create a separate FAT partition for sharing, and mount that inside your home directory in Ubuntu.

---

### Post by nikhilbhardwaj on 2009-08-10
i agree with you that fat cant handle permissions

but with vista and windows 7
ntfs seems to be handlinf file permissions
you cant just delete files anywhere as was the case with xp and below

---

### Post by Post Monkeh on 2009-08-10
xp had file ownership/permissions, but they manage them differently to linux. well i'd imagine so, since all my "private" files from xp are perfectly accessible when i boot using an ubuntu livecd.

---

### Post by asmoore82 on 2009-08-10
Unix, Linux, BSD, Solaris, and Mac OS X all follow the UNIX model for permissions - guess who doesn't.

[quote="humorix"]Given enough time and ***money***, eventually Micro$oft will re-invent UNIX.[/quote]
[emphasis added: begs the question: exactly who's money?]

---

