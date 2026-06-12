---
title: "copy my unbuntu off my usb stick onto another usb stick"
date: 2011-11-17
forum: General Help
---

### Post by brandyman52 on 2011-11-17
:)hi guys i would like to move all my stuff on my present usb stick on to a nano usb stick.the old one sticks out to much allways knocking it can you suggest how this can be done keeping all my settings folders etc would be gratefull for anybodys help thanks

---

### Post by WasMeHere on 2011-11-17
Welcome to the Ubuntu Forums, brandyman52,

If it is a boot drive (not simply a drive with data files) the easiest way is with dd, but it is risky, because dd is powerful and a tiny mistake might cause loss of data. You might even destroy your hard drive, so be sure what you do and that you select the correct input and output drives!

And even if you are sure, backup all valuable data before you start with dd. At the very least backup personal files (documents, photos ...)!

Run from another drive (for example your hard drive). Find out the addresses of your two USB drives
```
sudo fdisk -lu
df
```
The syntax is like this (assuming sd[COLOR="Red"]f[/COLOR] is your old USB drive and sd[COLOR="Red"]g[/COLOR] your new one)```
sudo dd if=/dev/sd[COLOR="Red"]f[/COLOR] of=/dev/sd[COLOR="Red"]g[/COLOR] bs=4096
```

If you get the [COLOR="Red"]red[/COLOR] letters wrong you will destroy data, so be very careful!

*Edit: Another alternative, that may feel more secure, is to download Clonezilla and use that to clone your USB drive to another one. That way you will also get a good general tool to make images for backup your whole computer.*

Have fun finding out about Ubuntu :-)
Olle

---

### Post by Elfy on 2011-11-17
Thread moved to General Help.

---

### Post by brandyman52 on 2011-11-17
> **Olle Wiklund said:**
> Welcome to the Ubuntu Forums, brandyman52,

If it is a boot drive (not simply a drive with data files) the easiest way is with dd, but it is risky, because dd is powerful and a tiny mistake might cause loss of data. You might even destroy your hard drive, so be sure what you do and that you select the correct input and output drives!

And even if you are sure, backup all valuable data before you start with dd. At the very least backup personal files (documents, photos ...)!

Run from another drive (for example your hard drive). Find out the addresses of your two USB drives
```
sudo fdisk -lu
df
```
The syntax is like this (assuming sd[COLOR="Red"]f[/COLOR] is your old USB drive and sd[COLOR="Red"]g[/COLOR] your new one)```
sudo dd if=/dev/sd[COLOR="Red"]f[/COLOR] of=/dev/sd[COLOR="Red"]g[/COLOR] bs=4096
```

If you get the [COLOR="Red"]red[/COLOR] letters wrong you will destroy data, so be very careful!

*Edit: Another alternative, that may feel more secure, is to download Clonezilla and use that to clone your USB drive to another one. That way you will also get a good general tool to make images for backup your whole computer.*

Have fun finding out about Ubuntu :-)
Olle
thanks for your quick reply i will try clonezilla better safe than sorry i will let you know how i got on thanks again

---

### Post by brandyman52 on 2011-11-20
got all my stuff over to the other usb thanks for your help olle

---

### Post by WasMeHere on 2011-11-20
I'm glad it worked. Please mark the thread SOLVED

Have fun finding out :-)
Olle

---

