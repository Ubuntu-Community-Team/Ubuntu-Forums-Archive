---
title: "fstab help..."
date: 2010-04-03
forum: General Help
---

### Post by jlubey on 2010-04-03
hey guys,
im new to ubuntu, but lovin it so far. currently triple booting snow leopard, window 7 ultimate, and kubuntu 9.1
my problem is this: my fstab file got pretty messed up. i was trying to create two icons on the desktop that would link to my mac osx partition, and to my windows partition (similar to the my computer link in windows, and how hard drives are displayed on the desktop in osx) I was having trouble setting an icon for the OSX link (i did not have permissions), so i tried chowning the partition and using the pysdm utility to give me the right permissions. im not sure what i did, but now the OSX partition will not mount at all. the windows one is working fine and i am happy with the shortcut i created. i searched a bit and decided to see what the fstab file said. somehow, my osx partition is now listed in there four times!!! i dont know much about this, but that seems pretty screwed up to me.

what i wanna know is, is there a way to ¨reset¨ the fstab file, essentially resetting it to defaults?? (as if it had just been installed on a new system) I have no idea what happened to it or what to do to fix it. i listed the entire contents of my fstab below, hope that gives you a better idea.

Thanks!

etc/fstab:

\# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                proc         defaults               0  0  
# / was on /dev/sda3 during installation
UUID=f80ae4c3-741c-475c-8c40-e6d6423abab1  /                    ext4         errors=remount-ro      0  1  
/dev/scd0                                  /media/cdrom0        udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sda1                                  /media/sda1          vfat         owner,users,user       0  0  
/dev/sda2                                  /media/Macintosh HD  hfsplus      defaults               0  0  
/dev/sda4                                  /media/Windows7      ntfs         defaults               0  0  
/dev/sda2                                  /media/Macintosh HD  hfsplus      defaults               0  0  
/dev/sda2                                  /media/Macintosh HD  hfsplus      users,user,owner       0  0  
/dev/sda2                                  /media/Macintosh HD  hfsplus      defaults               0  0

---

### Post by prodigy_ on 2010-04-03
Post the output of ```
sudo fdisk -l
``` and ```
sudo blkid
```

And also ```
ls -al /media
``` because this "Macintosh HD" part doesn't seem right. Need to see how the mount point in /media is actually called. If it indeed has a whitespace in its name, the whitespace needs to be escaped with a backslash when you refer to it: "Macintosh\ HD".

---

### Post by jlubey on 2010-04-03
sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02b5c88a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       22467   180255040   af  HFS / HFS+
/dev/sda3   *       22483       24307    14647296   83  Linux
/dev/sda4           24307       30402    48958464    7  HPFS/NTFS


sudo blkid:

/dev/sda1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat"
/dev/sda2: UUID="b5da32a0-af1e-3774-b466-8b6685adbe8c" LABEL="Macintosh HD" TYPE="hfsplus"
/dev/sda3: UUID="f80ae4c3-741c-475c-8c40-e6d6423abab1" TYPE="ext4"
/dev/sda4: UUID="52DE095EDE093BAB" LABEL="Windows 7" TYPE="ntfs"

---

### Post by prodigy_ on 2010-04-03
1. Check that **/media/Macintosh HD** directory exists.

2. Make a backup copy of fstab.

3. Try to replace its contents with this:

```
UUID=f80ae4c3-741c-475c-8c40-e6d6423abab1 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
UUID=70D6-1701 /media/sda1 vfat owner,users,user 0 0
UUID=b5da32a0-af1e-3774-b466-8b6685adbe8c /media/Macintosh\040HD hfsplus defaults 0 0
UUID=52DE095EDE093BAB /media/Windows7 ntfs defaults 0 0
```
\040 is octal for ASCII whitespace and UUIDs are the more correct way to mount partitions anyway.

---

### Post by jlubey on 2010-04-03
ok ill try that, and in the meantime here is:

ls -al /media

total 41
drwxr-xr-x  8 root    root  4096 2010-04-03 04:22 .
drwxr-xr-x 25 root    root  4096 2010-04-02 10:43 ..
lrwxrwxrwx  1 root    root     6 2010-02-13 22:51 cdrom -> cdrom0
drwxr-xr-x  2 root    root  4096 2010-02-13 22:51 cdrom0
lrwxrwxrwx  1 root    root    45 2010-02-13 22:51 .directory -> /etc/kubuntu-default-settings/directory-media
-rw-r--r--  1 root    root     0 2010-04-03 04:22 .hal-mtab
lrwxrwxrwx  1 root    root    42 2010-02-13 22:51 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxr-xr-x  2 jblubey root  4096 2010-04-02 18:04 Macintosh HD
drwxr-xr-x  3 root    root   512 1969-12-31 16:00 sda1
drwxr-xr-x  2 jblubey root  4096 2010-04-02 18:02 sda2
drwxr-xr-x  2 root    root  4096 2010-04-02 17:55 sda4
drwxrwxrwx  1 root    root 16384 2010-04-02 18:25 Windows7

---

### Post by prodigy_ on 2010-04-03
Ok, it looks right. On a side note, that mount point doesn't have to be called "Macintosh HD". It can actually be anything - "/media/MHD", for example. :-)

Now about permissions. You should change permissions on **the mount point**, not on the whole mount. :-) For this, you need to **unmount** the partition and use something like: ```
sudo chown -R $(id -u):$(id -u) /media/Macintosh\ HD
sudo chmod -R 777 /media/Macintosh\ HD
```

---

### Post by jlubey on 2010-04-03
ok heres the thing... i copied and pasted what you posted into the fstab file, and that seems to work. however, now in my root /media/ folder i have 3 folders, one that says sda2 (which is my osx partition location), one that says Macintosh\040HD, and one that says Macintosh HD. the sda2 folder and the Macintosh\040HD folders are both empty, should i just delete them?? (i would actually have to get ownership first because it says i dont have permission to modify). the Macintosh HD folder correctly shows the contents of my osx partition, so that is all good, i just wanna know how to get rid of the other two folders (NOTE: in sudo pysdm it shows that the sda2 partition is named Macintosh\040HD)

---

### Post by prodigy_ on 2010-04-03
Hmm. Strange, that it worked this way. :-) According to fstab manpage \040 should be interpreted as whitespace.

Anyway, I must admit I've never used mount points with whitespaces in their names, partly because I like to keep things simple. :-)

So. I'd do the following: ```
sudo umount UUID=b5da32a0-af1e-3774-b466-8b6685adbe8c
``` ```
sudo mv /media/Macintosh\ HD /media/MHD
``` ```
sudo rmdir /media/Macintosh\040HD
```

After that the line in fstab will need to be edited to look like: ```
UUID=b5da32a0-af1e-3774-b466-8b6685adbe8c /media/MHD hfsplus defaults 0 0
```

The rest of unused dirs in /media you can delete.

---

### Post by jlubey on 2010-04-03
ok thank you so much!! i followed your directions exactly (except i substituted MacintoshHD (no space) instead of MHD). everything is looking perfect, except for one last thing. when i go to change the icon of the new MacintoshHD folder inside the /media/ folder, i get the message:
Could not save properties. You do not have sufficient access to write to /media/MacintoshHD/.directory.

how do i take permission of that? is it just a chown or what?

---

### Post by cthlhu1987 on 2011-01-09
***_[This]("http://www.tuxfiles.org/linuxhelp/fstab.html")_*** is a really detailed and easy-to-understand tutorial about the fstab file.

---

