---
title: "Gaim Help...!!!"
date: 2006-04-19
forum: General Help
---

### Post by morbid_bean on 2006-04-19
I want to upgrade from the version of gaim i have (v1.5.0) To version 2.0.0beta3.
It dosnt matter how I do it, if i gotta uninstall old one and put new one in, or just upgrade, however is the easyist can you please tell me how to go about doing this...im a  noob to linux.

---

### Post by Sef on 2006-04-19
Read this wiki on how to compile gaim.  

[https://wiki.ubuntu.com/CompileGaim?highlight=%28compile%29]("https://wiki.ubuntu.com/CompileGaim?highlight=%28compile%29")

---

### Post by morbid_bean on 2006-04-19
ok i went to the wiki help thingy and when i get to the part whre i type  "sudo apt-get install checkinstall" i get an error:  "E: Couldn't find package checkinstall
"  Please help me.

---

### Post by PapaWiskas on 2006-04-19
sounds like your repositories might not all be selected.  Do a search on adding repositories.

---

### Post by dreamsINdigital on 2006-04-19
Or you can just go here and get the .deb.  The download link isn't working for me anymore though.
[http://www.ubuntuforums.org/showthread.php?t=152457](http://www.ubuntuforums.org/showthread.php?t=152457)

---

### Post by morbid_bean on 2006-04-19
I selected the resporties using the tutorial from   [https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29) and it still dose this BS to me.

---

### Post by dmizer on 2006-04-19
try this

uninstall your current gaim.

then go here -> [http://mighmos.org/packages.php](http://mighmos.org/packages.php)
Download both the i386 package (or the AMD64 package) as well as the "Data files"
then do this:
```
cd <your download directory>
sudo dpkg -i gaim-data_2.0.0-1beta3_all.deb
sudo dpkg -i gaim_2.0.0-1beta3_i386.deb
```
these packages are not perfect, but they work for me.  my biggest problem so far has been that i am unable to get either libnotify or guifications to work with this build, but i am neither skilled enough to do it myself nor do i posess the necessary patience.

---

### Post by dreamsINdigital on 2006-04-19
[QUOTE=dmizer]
these packages are not perfect, but they work for me.  my biggest problem so far has been that i am unable to get either libnotify or guifications to work with this build, but i am neither skilled enough to do it myself nor do i posess the necessary patience.[/QUOTE]
Use the package from the thread I provided and they will work.  But the problem is, the link is down.

---

### Post by PapaWiskas on 2006-04-20
[QUOTE=Sef]Read this wiki on how to compile gaim.  

[https://wiki.ubuntu.com/CompileGaim?highlight=%28compile%29]("https://wiki.ubuntu.com/CompileGaim?highlight=%28compile%29")[/QUOTE]


Thanks for this link Sef....this was the first time I EVER compiled anything.
Worked fine for me...hope to test file transfer out, hopefully it works, if only I had a buddy to test it with.  Everyone I know is asleep already....LOL

---

### Post by morbid_bean on 2006-04-20
Im getting really frustrated here.......how the heck to i access the desktop with terminal?

---

### Post by dreamsINdigital on 2006-04-20
cd Desktop

---

### Post by morbid_bean on 2006-04-20
this is getting old it dosnt matter how i do this i alway get some error!!:mad:

---

### Post by dmizer on 2006-04-20
unlike windows, linux command line is case sensitive.  if desktop is listed as Desktop, cd desktop will not work.  only cd Desktop.

---

### Post by morbid_bean on 2006-04-20
ok i got it working now all i had to do was say to my computer verbaly is "computer...if you dont start cooperating ill put windows xp back in you" and i tried it again and whoosh it works lol

---

### Post by Blunts on 2006-04-20
Now that last post is funny... sorry for the post to raise this in rank but a threat to install M$ whatever is enuff to scare any comp. =D>

---

### Post by dmizer on 2006-04-20
by the way.  the debian package created by the wiki compile-it-yourself how to won't run in breezy because of a non-existant shared library libdbus-glib-1.so.2 .

---

### Post by Sef on 2006-04-20
Papawiskas

> Thanks for this link Sef....this was the first time I EVER compiled anything.
Worked fine for me.

You're welcome.  Compiling is not easy, but sure a nice feeling when you can do it.

---

