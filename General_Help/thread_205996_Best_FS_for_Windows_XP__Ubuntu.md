---
title: "Best FS for Windows XP / Ubuntu?"
date: 2006-06-29
forum: General Help
---

### Post by tonyr1988 on 2006-06-29
I am dual-booting my system, and would like partitions like this:

1) Ubuntu system (ext3...or whatever it wants)
2) XP system (NTFS)
3) Files (???)

Where partition 3 needs to be able to be read / written by both XP and Ubuntu.

I had originally set up FAT32 for this purpose, because I thought it was the only one. But it shows up as VFAT in Ubuntu, and when I did the "sudo mount...", it wouldn't work.

How reliable is this: [http://www.fs-driver.org/](http://www.fs-driver.org/) ??? That would be cool to use ext2 in both.

So....fellow dual-booters, what do you use?

---

### Post by Maggot on 2006-06-29
I don't see why it shouldn't work. What command do you use to mount the fat32 partition in ubuntu? Any errors?

---

### Post by tonyr on 2006-06-29
FAT32 and VFAT are the same thing.  The line in **/etc/fstab** should use 
**vfat** for the file type.  From the command line:
```

mount -t vfat <device> <mount-point>

```

Heres one from my **/etc/fstab**
```

/dev/hda8       /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1

```

There is a driver or utility or some such for Windows that will let you read ext2/3
partitions.  I think it's called **fs-driver**, or something like that.  Search
the forums and the [wiki]("http://wiki.ubuntu.com")

---

### Post by Jucato on 2006-06-29
I use FAT32 for a shared partition. I didn't have any problems with mounting it. Maybe you could post the contents of /etc/fstab so that others could determine what's causing the problem.

Linux recognizes both FAT32 and FAT (older FAT version) as VFAT. so no problem there if Linux writes VFAT instead of FAT32.

I'm not sure about fs-driver, but I generally don't use plugins/additional software if I can use something native, like having a FAT32 partition. Of course, if you can't absolutely mount any FAT32 partition, then it might be the only option for you. I'm just saying that I try not to use it if I can.

---

### Post by x64Jimbo on 2006-06-29
[QUOTE=tonyr]FAT32 and VFAT are the same thing.  The line in **/etc/fstab** should use 
**vfat** for the file type.  From the command line:
```

mount -t vfat <device> <mount-point>

```

Heres one from my **/etc/fstab**
```

/dev/hda8       /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1

```

There is a driver or utility or some such for Windows that will let you read ext2/3
partitions.  I think it's called **fs-driver**, or something like that.  Search
the forums and the [wiki]("http://wiki.ubuntu.com")[/QUOTE]
Are you guys related? Very similar handles.

---

### Post by tonyr on 2006-06-29
fs-driver: see [http://www.fs-driver.org/]("http://www.fs-driver.org/").

To borrow a quote:
There are stranger things in heaven and earth, **x64Jimbo**,  than are dreamt of in our
philosophy.  (1988...I wish...)

---

### Post by Sgood1971 on 2006-06-29
[QUOTE=tonyr1988]How reliable is this: [http://www.fs-driver.org/](http://www.fs-driver.org/) ??? That would be cool to use ext2 in both.[/QUOTE]

I have been using it for quite a while now on a removable drive formatted ext2. It works great, the only problem that I see is if you remove the drive from you Windows box, Windows still displays a drive letter in My Computer even though it is not there. Not a biggie really, and.. It will not matter to you if you are gonna use it to dual boot anyway.

---

### Post by tonyr1988 on 2006-06-29
Wow....I feel retarded.

I wasn't thinking, and the location I told it to mount to was /mnt/hard drive
I guess the space was messing it up, because I re-did it under /mnt/maxtorhdd and it works beautifully. w00t w00t

Oh yeah, and nope - no relation between me and tonyr (that I know of). Just pure coincidence.

So, I've decided that I'm sticking with FAT32. I love it.

P.S. I haven't tried it - will it auto-mount my hard drive every time I boot up, or will I have to sudo mount it every time?

---

### Post by tonyr on 2006-06-29
If you have an entry for it in **/etc/fstab**, it should mount automatically
at every boot.

---

### Post by tonyr1988 on 2006-06-30
I don't see it in /etc/fstab

Also, when I have the fstab file open, it says read-only in the title bar, so I'm afraid to go throwing it in manually.

How can I get it added?

---

### Post by Jucato on 2006-06-30
the file fstab in the /etc/ directory is owned by root/administrator, so normal users (like you) don't have regular access to it. To be able to edit it, you need to launch gedit with root privileges. Press Alt+F2 and enter
```
gksudo gedit
```
Then  you can open /etc/fstab with write access.
Then just edit the line for your FAT32 partition to make it look like what the other tonyr wrote, of course, changing /dev/hda8 to wherever your FAT32 partition is.

---

### Post by tonyr on 2006-06-30
Do ALT-F2.  A **Run Application** window will appear.  Type in
**gksudo gedit /etc/fstab** and hit Enter.  Another window will open
requesting a password.  Enter **your** password. What you're doing here is
editing the file as **root**.  That's what **gksudo** does for you.  You can add the 
line, then save and exit.

Edit: oops. too slow.

---

### Post by se0siris on 2006-06-30
I used fs-driver quite happily for a while to mount an ext3 partition under WinXP. I moved over my Windows "My Documents" folders and all the user data on the ext3 drive and it all worked like a charm.

I'd planned to use FAT32, but it doesn't support files larger than 4Gb.

---

