---
title: "WinXP vs Ubuntu data transfer speed to USB stick"
date: 2011-05-20
forum: General Help
---

### Post by ke4ram on 2011-05-20
I have just purchased a Kingston 16G USB Stick. In Ubuntu 10.10 it took 23 minutes to copy a 274 MB Directory:mad:

Brought up WinXP. Took 47 seconds:popcorn:

Is there some reason for this:confused:

Thanks to anyone that answers...

---

### Post by ki4jgt on 2011-05-20
Don't think so. It usually takes 20 minutes for me to copy something from USB to HDD or vice versa in XP and only 2 to copy it in Ubuntu. Your system sounds mis-configured to me. This is definitely not routine behaviour.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Did you partition the device in Ubuntu or Windows? 

Try Ubuntu for Ubuntu Transfers.

---

### Post by TeoBigusGeekus on 2011-05-20
If the usb drive is ntfs, it's because of the conservatism in ntfs-3g.
Ntfs (writing) support for linux is relatively new, so it goes quite slow to avoid mistakes.
Format the drive as fat32, do the same transfer and notice the difference.

---

### Post by ke4ram on 2011-05-20
Did not partition at all. Just plugged it in. It's probably formatted MsDos.  I need it for work which of course uses Windows. 

Does it take that much computing to convert the file system?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Yes. It's made for Windows users, not Ubuntu users, so that's why.

---

### Post by Yaser. on 2011-05-20
I have a Kingston 8G usb stick, I think that ubuntu is faster than windows xp

---

### Post by linuxinstalledfromhdd on 2011-05-20
Use linux partitioned devices when you want to move from linux to linux systems. 

That's common sense.

---

### Post by ke4ram on 2011-05-20
@TeoBigusGeekus

You are so right... Knew it when I read it,,, Brain fart on this end. I'm a senior so that's the best excuse I can muster

Took about 40 seconds...maybe a bit faster than WinXP but I'm running Virtual XP so it may be a bit slower

Thanks ...

---

### Post by TeoBigusGeekus on 2011-05-20
You're welcome mate!
Unless you want to move files larger than 4gb (fat32's size limit) between linux and windows, stick to fat32.
Ntfs is a better file system, but its writing support is relatively new for linux.

---

