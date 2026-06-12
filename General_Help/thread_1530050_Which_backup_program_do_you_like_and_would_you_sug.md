---
title: "Which backup program do you like and would you suggest ?"
date: 2010-07-13
forum: General Help
---

### Post by AfrikaDietmar on 2010-07-13
Hi,

in windoz world i was using this neat program for my backups:
[http://www.traybackup.de/](http://www.traybackup.de/) (Page in German though...)

It took me back then a long time to find one like that.

Once a week i would run it for all folders on my hard drive and it would check with the old backup if anything changed and then update it. There were some little problems sometimes when the amount of data was several Gigabytes. 

What backup program would you recommend in ubuntu ? I use ubuntu 10.04.

I need to backup a PC that i have setup as a fileserver, and then 1 laptop with several user accounts who have their files.

The best would be to run backups daily or every second day. Here where i am based there are frequent electricity cuts which could mean at anytime the PC could break down, data loss. I would backup on a USB external drive. 

Backups will be several gigabytes. There are also files that can be above 1 GB. There are also folders with thousand of files without any sub folders.

What would you suggest ? Do you have any favorites, or some programs that have got speed when making file checks and updating the backup ?

---

### Post by inameiname on 2010-07-13
Rsync does that very same thing. And it's already installed on your Ubuntu system.

Grsync is the gui for it, which can be installed:

sudo apt-get install grsync

Personally, I use remastersys, but that's just me.

---

### Post by mike555 on 2010-07-13
I use "LuckyBackup" it's in package manager .

---

### Post by scouser73 on 2010-07-13
I use Pybackpack, it's also in the repositories.

---

