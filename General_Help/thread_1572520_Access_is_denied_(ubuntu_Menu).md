---
title: "Access is denied (ubuntu Menu)"
date: 2010-09-11
forum: General Help
---

### Post by hotshot247 on 2010-09-11
i put a windows program on my ubuntu pc and it's a portable program so i had to add a shortcut to the menu myself, well, i got the shortcut added but when i click it, it says that it cannot access it and it also says Permission Denied. i know it's probably something simple to fix that but i'm just not getting it. any help would be appreciated. thanks!

---

### Post by jv2112 on 2010-09-11
Post the output of 

ls -lh FILENAME

My guess is that it is set locking you out. 


You can change by->

sudo chmod 755 FILENAME  (User/Owner = RWX / Group=RX / Others=RX)

Chart->
r-w-x

4-2-1

U-G-O

Hope this helps.

---

### Post by hotshot247 on 2010-09-11
this is what it says when i type ls -lh FILENAME, 
-rw-r--r-- 1 chris chris 338K 2010-07-01 02:08 NUS Downloader.exe

and i tried to type chmod 755 and the filename, and then when i click the shortcut in the menu, it doesn't do anything, it doesn't even display an error. i know the program works because i can click the .exe file and the program opens.

---

### Post by jv2112 on 2010-09-11
If you did the chmod command then you will have permission to execute. However this does not appear to be the correct file. 

> 

-rw-r--r-- 1 chris chris 338K 2010-07-01 02:08 NUS Downloader.exe



If this is installed under wine then it would be hidden under your home directory. You could change the options in nautilus to show hidden files then you can do some digging to find the launcher.


Hope this helps.

---

### Post by hotshot247 on 2010-09-11
yea, it's the launcher. it's also a portable program which means that it doesn't install. it just runs wherever you copy the files to. it's good for running off of a flash drive but i just wanted to copy it to the hard drive and run it.

---

### Post by jv2112 on 2010-09-11
Is it associated with Wine ?

Try right clicking and select the "open with" option and choose wine.

---

### Post by hotshot247 on 2010-09-11
i just want to let you know that i figured it out. i feel like an idiot. lol all you have to do is when you make the shortcut in the menu, you have to type wine before the location of the file since it is ran through wine. thanks for your help though!

---

### Post by jv2112 on 2010-09-11
Cool 8)

---

