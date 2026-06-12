---
title: "Windows can't read USB pendrive after using it repeatedly in Ubuntu"
date: 2009-07-21
forum: General Help
---

### Post by Nugar on 2009-07-21
Hi all,

Since a few months age, I use Ubuntu (currently 9.04) exclusively at home and Linux Mint 7 on my laptop.

I depend a lot on my USB pendrive to keep some important files and read them between computers, including my Windows XP-based office PC. All the files are backed up.

But since yesterday, Windows can't read the USBs. When doing a "properties" it shows used space, but the files themselves can't be seen. Any new file I write is seen, but not the old ones.

I have not formatted the pendrive under Ubuntu nor done any other actions regarding the pendrive.

Any clues as to what can be happening? What I'm planning to do is reformat using FAT32 and copy the files back to the drive. Any advice before I do that?

Thanks in advance,

Nugar

---

### Post by nikhilk on 2009-07-21
Just to clarify, windows can't read USB pendrive but Ubuntu can? Have you tried reading the USB stick on multiple machines?
There was a recent [thread]("http://ubuntuforums.org/showthread.php?t=1211872") on a similar topic see if it helps.

---

### Post by Nugar on 2009-07-21
Hi nikhilk,

Yes, Ubuntu can read it, but Windows can't. And yes, I've tested on several Windows-based machines. No go :(

I'll read the other thread, thanks.

Cheers,

Nugar

---

### Post by Nugar on 2009-07-21
Hmm, it's interesting that I ran checkdisk and no dice. But I ran the defrag utility under windows and it shows the directories, yet explorer won't see them.

---

### Post by monikgtr on 2009-07-21
Something similar happened to me, I never thought it'd have to do something with Ubuntu though.. anyway, Windows won't open my usb if i double click on it, but right click-> explore will do it.

Hope it helps ;)

---

### Post by Nugar on 2009-07-21
Thanks monikgtr,

 It didn't work, so I ended formatting the drive. I used gparted in Ubuntu. btw, now the 1.91gb area won't mount in Ubuntu. Sandisk drive come with a small 8mb partition and a larger one.

So what I'll do is try it in Windows tomorrow (I actually have Windows in this box. I can dual boot, but I'm too lazy to do that, plus Ubuntu rocks) and if it doesn't show, I'll reformat again there. And once I come here, I'll load it with the backup.

Cheers,

Nugar

---

