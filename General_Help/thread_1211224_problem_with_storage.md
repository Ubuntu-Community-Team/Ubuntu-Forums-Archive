---
title: "problem with storage"
date: 2009-07-12
forum: General Help
---

### Post by Aboelnour on 2009-07-12
peace upon you:
when i was creating a backup for my system throw this command 
> tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
and it working but i notice the file become very big 2 gigabyte
so i terminate the operation with ctrl+c in terminal
and i deleted the backup file
but when i check my disk storage i saw  it is full 
i make a scan to know which folder take the huge space 
there is a surprise the "/" take 4.3 giga and he tell me that i use 7 giga 
what's the problem !!!!!!!?
thanks in advance :)

---

### Post by dumblebee100 on 2009-07-12
well you may not fully delete that file .

I think that file is still out there may be in trash ..
or it can be in locations like /tmp  and /var 

check /var folder full depth ..

I dont know how much this solves your problem ....but when I used fedora and kde 3.4 

I deleted movies but they are really not getting deleted instead they got stored in one of those directories ...so just check or you may do one thing ..

just search the file name in those directories that would be much easier

---

### Post by Aboelnour on 2009-07-12
> **dumblebee100 said:**
> well you may not fully delete that file .

I think that file is still out there may be in trash ..
or it can be in locations like /tmp  and /var 

check /var folder full depth ..

I dont know how much this solves your problem ....but when I used fedora and kde 3.4 

I deleted movies but they are really not getting deleted instead they got stored in one of those directories ...so just check or you may do one thing ..

just search the file name in those directories that would be much easier

first: really thanks for your fast reply
second: i already checked the trash && /var && /tmp
and found nothing 
i scan /var && /tmp && i found they normal
so what can i do?
i'm a ubuntu 8.10 user 
again thanks :)

---

### Post by dumblebee100 on 2009-11-14
I dont have much options for you to tell now but I think some of these may work 

some time back when I was using gnome I saw a app which tells us about the usage of the disk I mean each and every file and gives us a nice graph ..I think its name is DISK ANALYZER 

just open it from the root user then u can find the file I hope 

if you are successfull then inform me

---

