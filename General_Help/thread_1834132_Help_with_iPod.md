---
title: "Help with iPod"
date: 2011-08-27
forum: General Help
---

### Post by x371322 on 2011-08-27
I'm trying to get my iPod Nano 5g to sync within Ubuntu 11.04. This is driving me up the wall here.

It's formatted within Windows, FAT32, because it wouldn't even mount with the Mac format. I've already disabled journaling. Every app I've tried (banshee, rhythmbox, amarok, clementine, gtkpod) does the same thing. It shows the files syncing, says it's syncing on the iPod, and when it's finished the files show up within the app. Once I disconnect it to use it, however, NO SONGS. 

I don't get it. I've googled till blue in the face, but nothing I find seems to work. I've installed every package that seemed relevent (libimobiledevice and all that). I'm out of ideas.

Thanks.

---

### Post by x371322 on 2011-08-27
Bump.

---

### Post by x371322 on 2011-08-27
Finally got it working! Just in case it might help someone else, here's how I did it.

After playing with it more in gtkpod, I got an error that said something about a missing hash file. So I searched that error, and it brought me to this page:

[http://ubuntuforums.org/showthread.php?t=1267180&page=34](http://ubuntuforums.org/showthread.php?t=1267180&page=34)

Just follow the instructions in post 333. Be sure to restart your computer when done, mine wouldn't work until I did. Now it's syncing just fine in Banshee. Haven't tried it in the other apps yet.

---

