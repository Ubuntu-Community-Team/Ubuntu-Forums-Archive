---
title: "any way to recover brasero truncated files?"
date: 2010-11-22
forum: General Help
---

### Post by drz400e on 2010-11-22
[FONT=Times New Roman][SIZE=3]Hi! First post, new to the forum and to Linux. I have a lot of reading to do... I'm hoping you guys can help me out with a problem...[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]I used a bootable usb (Ubuntu 10.10) to backup files from an infected windows machine. I made backup DVD's using Brasero and disabled full windows compatibility when burning them to disc. The really dumb part was I didn't check the DVD's before I reinstalled windows on the drive I was backing up. They were all there, I assumed they were ok. The files on the DVD's (mix of doc, xls, jpg, etc.) won't open in windows or Linux. Anybody know of a way to recover them? [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]From what I've been reading, it seems like I'm screwed, but I thought I'd check with the experts. Is there a specific way Brasero/Linux changes the file, and can that info can be used to change it back? I assume it just cuts the name/header to 64 characters and I'm SOL. I'm going to see what diskdoctor's recovery software can get back from the hard drive. [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Any ideas are appreciated. Thanks![/FONT][/SIZE]

---

### Post by searchfgold6789 on 2010-11-22
A better idea might have been to use testdisk to copy the files to your RAM from the Live USB, and then burn the DVD's, and then repeat :)
Actually, you might even still be able to use testdisk to some extent...

Anyway. If you used Brasero from the Live USB, instead of a full installation of Ubuntu on a USB stick or hard disk, then there is no way to recover your files. This is because the Live USB uses your RAM as a hard disk, and you can't recover files from your RAM, because you have probably used your RAM alot since then, and besides it just isn't possible :(

I wish you luck.

---

### Post by drz400e on 2010-11-22
...besides it just isn't possible :sad:
 
nice way to sum it up. thanks for the response. 
 
on the bright side, it looks like the recovery software will get some of this stuff back, along with a lot of junk, but that's better than nothing.

---

