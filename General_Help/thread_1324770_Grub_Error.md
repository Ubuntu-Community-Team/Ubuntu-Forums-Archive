---
title: "Grub Error"
date: 2009-11-12
forum: General Help
---

### Post by Zorian144 on 2009-11-12
*

---

### Post by bashphoenux on 2009-11-12
insert your Windows CD and delete the ubuntu partition and restart :)

---

### Post by ranch hand on 2009-11-12
Let us review, YOU installed Ubuntu and over wrote the mbr on YOUR box.

YOU then deleted the bootloader.

Now, YOU are on an Ubuntu forum, being snippy and hostile, asking how to rescue some off brand OS.

I would try being polite to start with.

Secondly you need your MS install disk to repair your MBR to using the MS bootloader.

---

### Post by Zorian144 on 2009-11-12
I have my disk, it's not doing anything. I put repair and click repair start-up. It didn't do anything at all. Ubuntu broke my Mp3 Player and now my computer.

---

### Post by Zorian144 on 2009-11-12
*

---

### Post by mick55 on 2009-11-12
You haven't told us what version of windows you are 
using.The repair technique differs depending on the
Windows version.

Since the majority of Windows users are on XP
I will give you directions for that.

Boot the Windows XP CD.
Select repair.
Select Recovery Console.
After login at the command prompt run these commands
```
fixmbr
```then
```
fixboot
```then reboot and remove the CD.

Grub wiil be gone, you will boot straight into Windows.

If you have a different version of Windows please specify
which one.

---

### Post by RJ12 on 2009-11-12
By the way Ubuntu I am sure didnt break your MP3 player. If anything did you ask for help. By the way if you want help please be polite the community is not payed to do this we do at the generosity of our hearts so when i say please be more nice about it then please do so. What happened to your MP3 player I dont know but if you posted im sure someone will figure it out. Also if you want to be rude to us well then fine but dont expect much from us


Hope your happy with your Windoze whatever (you never said which one and...)

---

