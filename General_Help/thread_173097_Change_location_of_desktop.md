---
title: "Change location of desktop?"
date: 2006-05-09
forum: General Help
---

### Post by jms830 on 2006-05-09
I want to change my desktop to show the location /media/hdb1
how can I do this? I know I can change it to my home directory with configuration editor, but I don't want that. Thanks

---

### Post by felipe on 2006-05-10
[QUOTE=jms830]I want to change my desktop to show the location /media/hdb1
how can I do this? I know I can change it to my home directory with configuration editor, but I don't want that. Thanks[/QUOTE]

sudo mount -o bind /media/hdb1 /home/jsm830/Desktop

and/or add this line to /etc/fstab to make it permanent:

/dev/hdb1       /home/jsm830/Desktop        auto      bind        0       0

by the way, in a related topic, have you considered eliminating the Desktop directory and using your home as the Desktop? It's my default setting and I'm very happy with that. check /apps/nautilus/preferences/desktop_is_home_dir with gconf-editor :)

---

### Post by ryanakca on 2006-05-10
try this:
cd ~
mv Desktop Desktop.bak
ln -s /media/hdb1 Desktop

Logout, then login... should work
Cheers,
ryanakca

EDIT: Nevermind... I forgot about automounting :)

---

### Post by Ramses de Norre on 2006-05-10
Mounting it on ~/Desktop will be faster then symlinking, but you wont have a /media/hdb1 nomore, you can only acces it through ~/Desktop.

---

### Post by jms830 on 2006-05-10
thanks. I decided to mount hdb1 as Desktop because my home folder is on a harddrive that isn't big enough to fit all my data (music, photos, etc). I guess I could change the location of my home, but I don't really know how to do that or if it being on another partition might mess some things up.

Edit: Perhaps I could mount hdb1 as /home/jms830/ and then check use home dir as desktop? All I would have to do is to move all my stuff in my current home folder to hdb1?

---

### Post by sbrody88 on 2007-11-08
Hey,
I accidentally deleted my Desktop directory, so now my home folder is being used as the Desktop...but I don't want that - I'd really like to get my Desktop back to the way it was.  Anyone have any ideas how to do this?  I tried simply creating a directory in my home folder named Desktop, but that wasn't enough - its just a directory named Desktop, my Desktop still shows icons from my home directory, not from the Desktop directory.  Any help would be greatly appreciated!

---

### Post by strabes on 2007-11-08
> **sbrody88 said:**
> Hey,
I accidentally deleted my Desktop directory, so now my home folder is being used as the Desktop...but I don't want that - I'd really like to get my Desktop back to the way it was.  Anyone have any ideas how to do this?  I tried simply creating a directory in my home folder named Desktop, but that wasn't enough - its just a directory named Desktop, my Desktop still shows icons from my home directory, not from the Desktop directory.  Any help would be greatly appreciated!

Hit Alt+F2, run gconf-editor. Then browse to apps > nautilus > preferences. Uncheck "desktop_is_home_dir."

---

### Post by sbrody88 on 2007-11-08
It isn't currently checked...  I tried checking it, restarting, then unchecking it and restarting again, but Desktop is still home directory...

---

### Post by strabes on 2007-11-09
Hmm, strange. By the way, please don't [double post](http://ubuntuforums.org/showthread.php?t=607458). I don't know of any other solutions besides deleting your ~/.gnome2 directory, which will erase all of your gnome settings. This might work though. I really have no idea though.

---

