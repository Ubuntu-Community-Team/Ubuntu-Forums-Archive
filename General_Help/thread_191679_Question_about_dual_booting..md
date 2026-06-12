---
title: "Question about dual booting."
date: 2006-06-07
forum: General Help
---

### Post by SSB on 2006-06-07
Do I have to have Windows and Linux on the same hard drive? Here's how I currently have it set up:

Hard drive 1 is COMPLETELY partitioned for Windows. Windows is ALREADY INSTALLED.

Hard drive 2 (slave drive) has 128 GB for media and 60 that I want to use for Linux.

I am currently using the Ubuntu Live CD. If I click the install icon, will I easily be able to install to the empty partition I just made on my 2nd HD?

---

### Post by scxtt on 2006-06-07
linux (any flavor) is good at working w/ existing partitions ... so you should be able to easily install Ubuntu and have it play nice w/ your existing windows partition and your "media" partition ...

you'll be able to boot both via grub and you'll have easy access to anything that isn't NTFS (don't know if NTFS read is a hassle, don't think so - but NTFS write probably isn't gonna happen) ...

@ one point i had XP and 5 different linux installs + a "media partition" all playing together across 3 different HDDs ...

---

### Post by SSB on 2006-06-07
lovely. what file system should I set my new 60 GB partition to, then?

---

### Post by scxtt on 2006-06-07
for linux, i suppose it's personal preference - i use ext3 (cause it's default :wink: ) - i'm not really up to speed on which is "better" ... generally if i know i'll be using windows AND linux, i'll use FAT32 for the windows partitions and ext3 for anything linux ...

i know ubuntu gives you lots of options, and the only other one i can remember using is reiser, but i don't know if there's a clear 'winner' ...

---

### Post by SSB on 2006-06-07
heh, ok, i'll go with ext3 then. I only know about ntfs and fat32.

---

### Post by SSB on 2006-06-07
and just for the record.. is the guide to dual booting in the help section the most extensive guide I can get? This is my first ever attempt at this and I would hate to mess anything up.

---

### Post by scxtt on 2006-06-07
don't know - haven't looked @ it myself, most of what i know about installing multiple OSs comes from just doing it (which isn't a good policy if you want to be CERTAIN not to mess anything up) ... but most good partitioning / formatting programs provide you w/ enough good info about what you're doing that WYSIWYG when you hit "continue" to part./format ...

just pay close attn. to the info it gives you and you should be fine ... i would say that if before it installs grub, if it doesn't detect your windows partition, be careful - there might be something wrong ... it will always have the same "address" and won't be lost, but it might be an indication of a potential problem ...

---

### Post by SSB on 2006-06-07
ok, i'll go through the install process and come back if I have any questions. thank you.

---

