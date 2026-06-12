---
title: "Strange files appeared in home folder"
date: 2010-08-02
forum: General Help
---

### Post by tjustleft on 2010-08-02
Just a bit ago I clicked on home folder in places on the applications menu. When nautilus cam up it hung for a few minutes trying to open the folder. When it stopped trying to load it only showed a blank page. I chose to show hidden files and it finally opened.
 
For the fun of it I tried to open home again and this time waited longer. It did finally show the contents along with over 4000 strange files that weren't there half an hour ago.

The new files are titled Document--shool-1.dat 1 being the number of the file. They go all the way to Document--shool-4821.dat I did have to do a hard shut down the other day. After that ran fsck and had a few corrupted image files but that was it. The errors were fixed and there have been no problems until today. There don't seem to be any of these files in other folders.

I am running ubuntu 8.04 with all current updates. Thanks :)

---

### Post by Smart Viking on 2010-08-02
Hi, this sounds like some bug or something, if you just want to remove the files, you could run these following two commands([COLOR=Red]WARNING[COLOR=Black]: this will delete ALL you .dat files in your home folder, if you have anyone that you might wanna keep, MOVE THEM TO ANOTHER FOLDER)[/COLOR][/COLOR]:

```
cd ~
```
```
rm *.dat
```
And if the above command gives you something like "blablabla only root can delete blabla are you root" or anything like that, just put "sudo" infront of the last command. I hope this helped. :)

---

### Post by tjustleft on 2010-08-04
Thanks! I just moved the files to a new folder. Home opens normally now. I just wonder what those files are and how they got there.

---

