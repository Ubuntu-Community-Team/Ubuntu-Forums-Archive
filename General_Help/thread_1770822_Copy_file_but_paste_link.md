---
title: "Copy file but paste link"
date: 2011-05-29
forum: General Help
---

### Post by Robbyx on 2011-05-29
Has anyone seen a seamless way to create a symbolic link via a GUI based file manager? I have been using PCManfm because I find it fast, but I can copy the file but paste a symbolic link instead of the actual file.

---

### Post by jerrrys on 2011-05-29
you will probally find it to heavy, but i use nautilus for that.  actually all that is needed is the dual pane option which there are many file managers to choose from.  if thats seamless enough for you, i have a list of these if you want it.

---

### Post by Robbyx on 2011-05-29
> **jerrrys said:**
> you will probally find it to heavy, but i use nautilus for that.  actually all that is needed is the dual pane option which there are many file managers to choose from.  if thats seamless enough for you, i have a list of these if you want it.

I like pcmanfm because it does not take forever to open the big bin directories. What is the fastest on your list?

---

### Post by jerrrys on 2011-05-29
gentoo and gnome-commander come to mind as good ones

---

### Post by Robbyx on 2011-05-29
> **jerrrys said:**
> gentoo and gnome-commander come to mind as good ones

Thank you. It is not terribly obvious how to copy and paste a link to a new folder when I start with a full file (not the link). How do I do it?

---

### Post by jerrrys on 2011-05-29
sorry, im not following you

---

### Post by Robbyx on 2011-05-29
What I was looking for was to be able to do the following:

Enable access to a file in another directory via a symbolic link in the other director. To make that easy i wanted to  create a link on the fly in the new location. I think windows allows this. You copy the file go to the additional location. Right click and create a link rather than copy the whole file.

---

### Post by jerrrys on 2011-05-29
if i want to go outside of my root directory a softlink will not work.  or i should say will work until you shut down and the links are broken. i do not run windows so don't know about that.

---

### Post by Robbyx on 2011-05-29
I do  not use windows any more.

I looked again at gentoo. In the second window opened the destination folder. In the first highlighted the file, clicked on the option to make link and a symbolic link  appeared in the second directory. I assume that it will survive a reboot. Than is what I wanted in the first place. 
Thanks

Robin

---

### Post by jerrrys on 2011-05-29
hope it works for you.  as for me, i went with rsync to an ext4 non-bootable hdd

---

