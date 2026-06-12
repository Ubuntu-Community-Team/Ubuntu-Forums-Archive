---
title: "Dissapearing folder"
date: 2012-03-17
forum: General Help
---

### Post by Sudarson4 on 2012-03-17
I have Lucid Lynx installed right now and a peculiar problem cropped up this morning - a folder from my Music folder is missing 

I checked the trash and tried looking for it in hidden files, but i couldn't find it. I wouldn't be so bother except for the fact that i have 4 gb of music in the folder, and really want it back. Any suggestions?

---

### Post by jerrrys on 2012-03-17
I didn't know that folders could disappear like that.

Open Nautilus and search your "filesystem" for it 

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=filesystem+search&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=filesystem+search&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nautilus+file+system+search&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nautilus+file+system+search&sa=Search&cof=FORID:9)

and welcome to the forums

---

### Post by Sudarson4 on 2012-03-17
i tried everything, can't find it

and thanks for the warm welcome :)

---

### Post by raja.genupula on 2012-03-17
ok use this link 
[http://www.unixtutorial.org/2008/03/find-large-files-and-directories/](http://www.unixtutorial.org/2008/03/find-large-files-and-directories/)
and search for that file with its in the actual directory where its kept .

---

### Post by Sudarson4 on 2012-03-18
no, i still don't get anything
i tried the 'du' command on terminal, but didn't get anything with that either

im starting to suspect vandalism now ...

---

### Post by raja.genupula on 2012-03-18
hey i know this gonna sounds funny but give a try my friend . in that xommand change the directory to "/" and then try again . make sure that all your partitions are mounted .

---

### Post by ubudog on 2012-03-18
Hi, welcome to the forums.  Do other people have access to your computer?

Also, try this: 
```
sudo updatedb && sudo locate nameoflostfolder
```
Do you see the name of your lost folder in the output?
(Be sure to type your password when prompted)

---

### Post by Sudarson4 on 2012-03-18
Mr. raja, i don't know what you mean, please forgive my incompetence, im only 15 and i've had ubuntu for only a couple of months

and ubudog, no, i didn't get anything. but yes, i do share the comp with my dad and brother, but both of them say that they haven't done anything

---

### Post by raja.genupula on 2012-03-18
```
sudo find / -size +4G
```
do that and make sure that all partitions  are mounted .

---

### Post by Sudarson4 on 2012-03-18
i only have one partition on my hard disk, so i don't think thats a problem, but when i give the command, this is what i get

sud@sudamson-desktop:~$ sudo find / -size +4G
[sudo] password for sud: 
find: `/home/draco/.gvfs': Permission denied
find: `/home/sud/.gvfs': Permission denied
find: `/proc/17199/task/17199/fd/5': No such file or directory
find: `/proc/17199/task/17199/fdinfo/5': No such file or directory
find: `/proc/17199/fd/5': No such file or directory
find: `/proc/17199/fdinfo/5': No such file or directory

---

### Post by Sudarson4 on 2012-03-18
i haven't fixed the problem, but i just copied the songs back from my ipod, so no worries :) 
but i would be more than glad to find out where my files went

---

