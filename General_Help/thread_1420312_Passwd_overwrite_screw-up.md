---
title: "Passwd overwrite screw-up"
date: 2010-03-02
forum: General Help
---

### Post by Tomasud on 2010-03-02
Ok, i don't know where else to go, I've spent several hours trying to get different systems to work with my box when i did something i shouldn't have! Trying to get vsftpd usergroups to work i accidentally moved a file called passwd from /etc/vsftpd/ to /etc/, resulting in my root access is destroyed!

So anyone have an idea on how to restore the passwd file so i can keep working, or do i have to re-install the entire box?

Any help is much appreciated!

---

### Post by sisco311 on 2010-03-02
Boot a LiveCD, mount root ("/") partition & replace the passwd file with the one of its backup files: [/mount/point]/etc/passwd- or [/mount/point]/var/backup/passwd.bak.

---

### Post by Tomasud on 2010-03-02
Cheers! I'm downloading a live cd now, one more thing however, there seems to be two passwd files one with a - at the end: passwd- , which one do i switch/remove?

---

### Post by sisco311 on 2010-03-02
> **Tomasud said:**
> Cheers! I'm downloading a live cd now, one more thing however, there seems to be two passwd files one with a - at the end: passwd- , which one do i switch/remove?

Oh sorry, passwd- is the backup file. You have to replace /etc/passwd with /etc/passwd**-**.

EDIT:
The content of the file should look like:
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
...
```

---

### Post by Tomasud on 2010-03-03
Thank you so much man! After having some problems with a live cd burnt in W7 buildt in burner, i got the live ubuntu 9.10 to work and having no clue what to do i mumbeled about uintill i figured that my hard drive was somewhere in media/hex code/ using su i overwrote the old passwd with what was inside passwd-, checking ofcourse that my user was present in the file. Now i can boot properly and log onto my user, with no problems! 

Ill post a small step by step of what i did incase someone else have this problem

1. load live-cd 
2. open computer and find the right disk
3. in the pane over the "explorer" there should be an arrow in the left corner of this pane, click it to reveal media, click this.
4. figure out which folder is your harddrive, (i had several mounted) right click it and go to properties
5. copy the name of the folder and open terminal
6. type in: sudo gedit /media/"harddrive code"/etc/passwd- 
7. check if your login is there, if not make the file as sisco331 suggested and go file-> save as
8. remove the - from passwd- and save/overwrite

This should be it, hope it helps. And thanks again to Sisco331 for helping me

-Thomas

---

