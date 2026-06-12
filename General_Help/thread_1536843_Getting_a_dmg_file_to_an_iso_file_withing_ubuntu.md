---
title: "Getting a dmg file to an iso file withing ubuntu"
date: 2010-07-22
forum: General Help
---

### Post by unckybob on 2010-07-22
This may be possible on a Mac but I don't have one. I got a Mac at a garage sale without a hard drive and I'm trying to install OS_X on it. I have the dmg, but I can't seem to get it into the form of an iso. 

So I'm trying to make an iso from a dmg file. I'm using directions at:

[https://help.ubuntu.com/community/Ma...s#DMG%20Images](https://help.ubuntu.com/community/Ma...s#DMG%20Images)

Here's what I did: 

> # dmg2img /path/to/example.dmg /path/to/example.img
# sudo mkdir /media/example
# sudo modprobe hfsplus
# sudo mount -t hfsplus -o loop example.img /media/example
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

# dmesg | tail
[26680.771684] ISO 9660 Extensions: Microsoft Joliet Level 1
[26680.771724] ISO 9660 Extensions: IEEE_P1282
[27124.100425] ISO 9660 Extensions: Microsoft Joliet Level 1
[27124.100468] ISO 9660 Extensions: IEEE_P1282
[28357.335773] ISO 9660 Extensions: Microsoft Joliet Level 1
[28357.335815] ISO 9660 Extensions: IEEE_P1282
[28450.349967] hfs: unable to find HFS+ superblock
[28561.190876] ISO 9660 Extensions: Microsoft Joliet Level 1
[28561.190917] ISO 9660 Extensions: IEEE_P1282
[29185.381953] hfs: unable to find HFS+ superblock 


I'm doing all this on an ext2 partition if that matters.

I don't have any experience with this kind of thing. Can someone help?

---

### Post by Darkness Des on 2010-07-22
Make sure that you're using the actual paths to your DMG and IMG files, and not just copying and pasting the examples in the tutorial. There's a very good chance that this is your problem.

---

### Post by unckybob on 2010-07-22
I wasn't cutting and pasting. I'm sure I got the paths right.

---

### Post by unckybob on 2010-07-24
I used: 

# sudo mount -o loop example.img /media/example

Instead of: 

# sudo mount -t hfsplus -o loop example.img /media/example

That I used above. I guess the "-t hfsplus" option means that the file your trying to mount is an hfs+ filesystem. The file "example.img" was actually on a linux partition. 

Thanks.

---

