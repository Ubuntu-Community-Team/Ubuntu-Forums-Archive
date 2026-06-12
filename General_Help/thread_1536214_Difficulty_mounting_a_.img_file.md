---
title: "Difficulty mounting a .img file"
date: 2010-07-21
forum: General Help
---

### Post by unckybob on 2010-07-21
I am trying to mount a .img file as described in: 

[https://help.ubuntu.com/community/ManageDiscImages#DMG%20Images](https://help.ubuntu.com/community/ManageDiscImages#DMG%20Images) 

I used: 

# sudo mkdir /media/example 
# sudo modprobe hfsplus
# sudo mount -t hfsplus -o loop example.img /media/example
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
# dmesg | tail 
[38203.131172] type=1505 audit(1279764235.588:18):  operation="profile_replace" pid=11083 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[38203.131279] type=1505 audit(1279764235.588:19):  operation="profile_replace" pid=11083 name="/usr/lib/connman/scripts/dhclient-script"
[38209.973017] type=1505 audit(1279764242.428:20):  operation="profile_replace" pid=11084 name="/usr/bin/evince"
[38210.004685] type=1505 audit(1279764242.458:21):  operation="profile_replace" pid=11084 name="/usr/bin/evince-previewer"
[38210.005740] type=1505 audit(1279764242.458:22):  operation="profile_replace" pid=11084 name="/usr/bin/evince-thumbnailer"
[38213.071974] type=1505 audit(1279764245.529:23):  operation="profile_replace" pid=11086 name="/usr/lib/cups/backend/cups-pdf"
[38213.072285] type=1505 audit(1279764245.529:24):  operation="profile_replace" pid=11086 name="/usr/sbin/cupsd"
[38213.276375] type=1505 audit(1279764245.728:25):  operation="profile_replace" pid=11087 name="/usr/sbin/mysqld-akonadi"
[38213.470030] type=1505 audit(1279764245.928:26):  operation="profile_replace" pid=11088 name="/usr/sbin/tcpdump"
[39129.675722] hfs: unable to find HFS+ superblock

This is on a second hard drive if that helps. 

I've have absolutely no experience with this sort of thing. Will someone please help me?

---

### Post by bigfatgooglefat on 2010-07-22
Alright, it seems you're having a problem with locating the .img file. When you do > # sudo mkdir /media/example and > sudo mount -t hfsplus -o loop example.img /media/example youre telling Ubuntu to open the file "example.img" in your home directory to the directory /media/example which you just made. 

I'm assuming that your problem is that either the .img isn't named "example.img", or that it's not in your home directory (as you said it's on a second drive). Find where it is and change the "example.img" to the location (ex: /media/externaldrive/example.img), and see if it works.

---

### Post by unckybob on 2010-07-22
Sorry I didn't get back sooner. I went to bed. Hope you're still out there. 

I tried moving it to my Desktop on the internal drive. Pretty much got the same thing. 

# sudo mount -t hfsplus -o loop /home/robert/Desktop/example.img /home/robert/Desktop/example 
 mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

# dmesg | tail 
[39129.675722] hfs: unable to find HFS+ superblock
[39326.520252] hfs: unable to find HFS+ superblock
[39453.311029] hfs: unable to find HFS+ superblock
[39792.110198] hfs: unable to find HFS+ superblock
[39815.560116] hfs: unable to find HFS+ superblock
[42910.160397] hfs: unable to find HFS+ superblock
[80728.293325] hfs: unable to find HFS+ superblock
[81230.164805] hfs: unable to find HFS+ superblock
[81542.042536] hfs: unable to find HFS+ superblock

---

### Post by unckybob on 2010-07-22
Been doing a little homework. Doesn't this assume that all this is being done on an HFS+ partition?

---

### Post by unckybob on 2010-07-22
I created an hfs+ partition on my drive. If what I need to do is transfer the dmg file onto the hfs+ partition, I can't seem to drop and drag them over once I have the partition mounted. Please help.

---

### Post by unckybob on 2010-07-22
New idea. Is it possible to create an hfs+ partion without journaling in Ubuntu?

---

### Post by unckybob on 2010-07-22
Please help me with this if you can. I don't have a mac computer, I'm trying to write the install img file to a usb drive so I can install it to a mac I got at a garage sale.

---

### Post by unckybob on 2010-07-24
Figured out that img files are really image files that are in a format for a flash drive. I used dd at the command line to burn it to my flash drive. 

That's one solved!

---

