---
title: "Install from FAT partition"
date: 2006-05-16
forum: General Help
---

### Post by madods on 2006-05-16
I want to put Ubuntu on an old laptop for my kids. The CD-ROM drive is dead so I've put the laptop HDD into my desktop PC and created a FAT partition with loadlin.exe, vmlinuz, initrd.gz and the .iso file in it. 

I can boot this partition in the laptop, run loadlin and get the installer running, bu I can't seem to convince it to use the .iso file for the install. It keeps complaining there is no Unbuntu CD-ROM mounted.

Any suggestions?

---

### Post by glotz on 2006-05-16
Sorry for this non-tech solution but wouldn't getting a working cd drive hooked be so much easier? ;)

---

### Post by madods on 2006-05-16
[QUOTE=glotz]Sorry for this non-tech solution but wouldn't getting a working cd drive hooked be so much easier? ;)[/QUOTE]
Yes, but much more expensive its a pre HP Compaq and I have no budget :-(

---

### Post by glotz on 2006-05-16
Yeah, I somehow managed to miss the laptop part... How about installing Ubuntu when the disk is on your desktop?

---

### Post by madods on 2006-05-16
[QUOTE=glotz]Yeah, I somehow managed to miss the laptop part... How about installing Ubuntu when the disk is on your desktop?[/QUOTE]
Won't that mean that the desktop hardware would be detected rather than the laptop's?

---

### Post by glotz on 2006-05-17
Sure but isn't the detection redoable? Would think so, say you install new hardware for example.

---

### Post by madods on 2006-05-22
I resolved this by using a USB adaptor to connect and IDE CDROM to the laptop. I could then start the installer with loadlin which found the install CD OK.

---

