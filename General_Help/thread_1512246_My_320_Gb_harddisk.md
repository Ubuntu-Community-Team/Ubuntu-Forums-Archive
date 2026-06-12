---
title: "My 320 Gb harddisk"
date: 2010-06-17
forum: General Help
---

### Post by Simdog1 on 2010-06-17
Well im trying to get RSPS working(runescape private server) since its like only game i can play on ubuntu since my windows vista dissapeared. so i installed java and try to run compile with wine but i get file not found so i double click it which opens with grub and it says
@echo off
"/home/family/Desktop/c:/Program Files/Java/jdk1.6.0_20/bin/javac.exe" *.java -cp .;./lib/sbbi-upnplib-1.0.4.jar;./lib/jxta.jar
pause


i notice that its in my c: drive so i go to my computer then click on my 320 hard drive but when it opens 
there is a file called lost+found which is the only file. so i double click on it and i get an error saying
You do not have the permissions necessary to view the contents of "lost+found". idk what it is  or why its there but i wanna get in to see if my java is in there 
or could you tell me what tio change so i can acess my java? thanks

---

### Post by sgosnell on 2010-06-17
You're trying to compile under wine?  If so, that won't work, AFAIK.  You didn't open anything with grub.  Maybe with gedit?  Is the game java based?  If it is, you don't need wine, java runs fine natively in Linux.

I really have no idea what you're doing or trying to do.  Clearer explanations might help.

---

### Post by Simdog1 on 2010-06-18
ya the game is a java based game but when i double click it it opens with gedit (not grub my mistake) and it has the path of where it is but my real question is how come when i open my hard sisk it has lost+found and when i try to open it i get this message. You do not have the permissions necessary to view the contents of  "lost+found". idk what that meant but help please

---

### Post by sgosnell on 2010-06-18
Lost&found is a folder owned by root that does what it says, keeps track of lost and found files.  You have to be root to view it.  You can do that by opening Nautilus as root, usually by opening a terminal and typing 'sudo nautilus', then entering your password when prompted.  What you're seeing is your home folder, not your entire HDD.  You won't see that in one place, most likely.  You'll only see the Ubuntu partition under normal use, and you'll have to mount the other partitions in order to access them.

---

