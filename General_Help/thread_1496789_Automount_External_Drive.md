---
title: "Automount External Drive"
date: 2010-05-29
forum: General Help
---

### Post by WilliamThrilliam on 2010-05-29
I want nautilus to automatically mount my external drive when ubuntu 10.04 starts.  This drive is encrypted, but the key has already been stored and all I have to do is click on it in my Places menu for it to mount.  

It mounts to:

/media/Will's Drive

I feel like I shouldn't have to edit fstab or anything like that.  If I can add it to my startup programs, that would be great, I just need to know the command to get nautilus to open up /media/Will's Drive at startup.

Thanks.

---

### Post by quixote on 2010-05-30
The only way I know to do it is using fstab, so I'll give you that way.  As far as I know, there is no way to do it using just nautilus.```
gksudo gedit /etc/fstab
```

Then add the following lines:
```
#automounted external drive             *[optional comment for identification. Put anything you want here.]*
/dev/sd*b**x* /media/WillsDrive *ext4* **auto**,user   0    0
```

sd*bx* should be replaced with the right designation for your drive.  Or replace the whole "/dev/sd*bx*" by UUID=*the-number* (It can be found by typing "sudo blkid" (without quotes) in the terminal.)

I'd strongly recommend renaming the directory in /media so that you don't have apostrophe and space in the name.  Those are both special characters, and if you really want to use them, they need to be "escaped".  I'm not sure what the right syntax is in fstab.  At the command line it would be something like /media/Will\'s\ Drive. 

Replace "ext4" with the filesystem on your drive.  If it's Lucid, it's most likely ext4.  If Windows, ntfs.  If an older ubuntu, ext3.  And so on.

The important part is the "auto".  That's the option that tells it to automount.  "user" means users besides root can mount it.  The two zeroes say how often to do various kinds of housekeeping on the drive.  In this case never.

There's everything you need for fstab in this [wiki page]("https://help.ubuntu.com/community/Fstab").

---

### Post by formaldehyde_spoon on 2010-05-30
You could add "mount /dev/sdbx /media/WillsDrive" to /etc/rc.local to mount on startup, but this seems a strange thing to do.
Just add it to fstab: this does exactly what you want - mounts the disk on boot.

---

### Post by WilliamThrilliam on 2010-05-31
First, let me say thank you to you both for answering my question :).

My drive is ext3 encrypted lucks.  I know the drive is identified as /dev/mapper/"some crazy alpha numeric" and not only would I have to modify fstab, but do some other things to /dev/mapper.  I have tried this before and all it has given me, and others as I have read, headaches.

Since Gnome now so kindly recognizes my luks drive and lets me store the key, I would love to just have it auto-mounted in Gnome.

---

### Post by formaldehyde_spoon on 2010-06-01
> **WilliamThrilliam said:**
> First, let me say thank you to you both for answering my question :).

My drive is ext3 encrypted lucks.  I know the drive is identified as /dev/mapper/&quot;some crazy alpha numeric&quot; and not only would I have to modify fstab, but do some other things to /dev/mapper.  I have tried this before and all it has given me, and others as I have read, headaches.

Since Gnome now so kindly recognizes my luks drive and lets me store the key, I would love to just have it auto-mounted in Gnome.

It's true a lot of people have trouble with fstab (I had some myself, very recently) but fstab really is what you should be looking at.

If you have trouble with fstab post your fstab file contents, and the results of "mount" and "sudo fdisk -l" and we will try to help.

---

