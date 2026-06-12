---
title: "Transferring Files &amp; Photoshop in Wine"
date: 2009-06-28
forum: General Help
---

### Post by ZombiesNTea on 2009-06-28
I actually have a few questions:

1) How do I transfer files from Windows to Ubuntu?  My primary use for Windows is iTunes for my iPod, and I keep doing it there because I have tons of music.  My external hard drive won't let me transfer the files (I'd have to reformat it to work for Ubuntu).  My hard drive is partitioned... is there some way to drag and drop or something?  I've tried accessing the other drive from each, but its not set up like theres folders just there to do that with or whatnot.

2) Does Photoshop 7 work with Wine, and if so, how would I install it on here?  Thats my other primary windows usage.  If both the question before this and this one are doable, I'd like to get rid of Windows on here.

3) I figure I might as well ask... can anyone help me on this question I asked elsewhere on here earlier?: [http://ubuntuforums.org/showthread.php?t=1199371](http://ubuntuforums.org/showthread.php?t=1199371)


Thanks!

---

### Post by DeMus on 2009-06-28
> **ZombiesNTea said:**
> I actually have a few questions:

1) How do I transfer files from Windows to Ubuntu?  My primary use for Windows is iTunes for my iPod, and I keep doing it there because I have tons of music.  My external hard drive won't let me transfer the files (I'd have to reformat it to work for Ubuntu).  My hard drive is partitioned... is there some way to drag and drop or something?  I've tried accessing the other drive from each, but its not set up like theres folders just there to do that with or whatnot.

2) Does Photoshop 7 work with Wine, and if so, how would I install it on here?  Thats my other primary windows usage.  If both the question before this and this one are doable, I'd like to get rid of Windows on here.

3) I figure I might as well ask... can anyone help me on this question I asked elsewhere on here earlier?: [http://ubuntuforums.org/showthread.php?t=1199371](http://ubuntuforums.org/showthread.php?t=1199371)


Thanks!


1)
Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

2)
Open Nautilus and look for the installaer program. Right-click it and choose open with wine. See if it works.

3)
No idea. Sorry

---

### Post by hermitcrabred on 2009-06-28
You seem to know a lot more that I do, before I changed to Ubuntu I backed up ITunes in a portable hard drive, I`ve been able to play songs on rhythombox but is there any way at all to transfer all my music to it in a one shot instead of doing it one by one? Also, can I use my IPod Nano with this program, I`m lost...Any help is appreciated. Thank you!

---

### Post by ZombiesNTea on 2009-06-29
> **DeMus said:**
> 1)
Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

2)
Open Nautilus and look for the installaer program. Right-click it and choose open with wine. See if it works.

3)
No idea. Sorry

Thanks a ton!

I did something wrong... I think I somehow mounted the U drive (Ubuntu is on U Drive, left Windows on C)... it wont let me unmount it.  I'm kind of Ubuntarded haha.

---

### Post by t4thfavor on 2009-06-29
I believe I have #3 handled also.

---

### Post by ZombiesNTea on 2009-06-29
> **ZombiesNTea said:**
> Thanks a ton!

I did something wrong... I think I somehow mounted the U drive (Ubuntu is on U Drive, left Windows on C)... it wont let me unmount it.  I'm kind of Ubuntarded haha.

When I go to unmount it, it says

[B]Cannot unmount volume

unmount: only root can unmount /dev/sda5 from /media/desktop[/B]

(media isn't a folder that im aware of on here)

---

### Post by ZombiesNTea on 2009-06-30
> **ZombiesNTea said:**
> When I go to unmount it, it says

[B]Cannot unmount volume

unmount: only root can unmount /dev/sda5 from /media/desktop[/B]

(media isn't a folder that im aware of on here)

What can I do?

---

### Post by ZombiesNTea on 2009-06-30
> **ZombiesNTea said:**
> What can I do?

Can I get this mounted version of the partition I have Ubuntu on off of my desktop?

---

### Post by ZombiesNTea on 2009-07-16
hello?

---

### Post by michy99 on 2009-07-16
```
sudo umount /media/desktop
```

---

### Post by ZombiesNTea on 2009-07-16
You rock!  Thanks a million!

---

### Post by ZombiesNTea on 2009-07-16
When I try to open the NTFS program, I get to the point where it says "Enable write support for internal device," I click okay and it is still just doing nothing.  It doesn't go to another window.

---

### Post by ZombiesNTea on 2009-07-16
If I uncheck the "internal device" option, it re-mounts the Ubuntu partition onto the desktop.

---

### Post by ZombiesNTea on 2009-07-24
And every time I restart Ubuntu, it is back on the desktop.

---

### Post by ZombiesNTea on 2009-08-01
> **ZombiesNTea said:**
> And every time I restart Ubuntu, it is back on the desktop.

?

---

### Post by ZombiesNTea on 2009-08-06
*bump*

I'd really like to *permanently* get rid of the "287.9 MB Media" off of my desktop (rather than go into the terminal to do it every time I turn the computer on, only to have it be there every time I turn the computer on).

---

