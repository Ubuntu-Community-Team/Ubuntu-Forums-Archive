---
title: "How do I make ipod mount NOT read only?"
date: 2010-01-29
forum: General Help
---

### Post by gruntlips_ on 2010-01-29
I have an old ipod classic. I am running 9.10 and use banshee 1.5.4 as my music player. I want to connect the ipod to banshee and download some music onto it (I know, I know..) When I click on the ipod icon in banshee I get this error.

"Your ipod is mounted read only. Banshee cannot restore your ipod."

How do I fix this problem? I am willing to do anything to the ipod (reformat it, yell at it, hide it under the couch, etc.) to make it work.

Thanks. I appreciate your help....

- gl

---

### Post by dcstar on 2010-01-30
> **gruntlips_ said:**
> I have an old ipod classic. I am running 9.10 and use banshee 1.5.4 as my music player. I want to connect the ipod to banshee and download some music onto it (I know, I know..) When I click on the ipod icon in banshee I get this error.

"Your ipod is mounted read only. Banshee cannot restore your ipod."

How do I fix this problem? I am willing to do anything to the ipod (reformat it, yell at it, hide it under the couch, etc.) to make it work.

Thanks. I appreciate your help....

- gl

Do a fsck on it.

---

### Post by gruntlips_ on 2010-01-30
yeah, that didn't solve it.

---

### Post by blueshiftoverwatch on 2010-01-30
Sounds like a permissions problem. If you want to change the permissions of a file/folder from the GUI you can:

1. Enter **gksudo nautilus** into the terminal
2. Right click on a file/folder or go into it and right click any white space where theirs not icons -> properties -> permissions
3. Change the owner to your username and select "create and delete files"
4. Change file access to "read and write"
5. Click "apply enclosed permissions to enclosed files"

---

### Post by [Linuxdave] on 2010-11-25
In the event that the gksudo nautilus does not work,  try this workaround on Meerkat:  1.  using a device manager (gtkpod of rhythmbox),  back up all the information of your ipod 2.  open (or download and open) disk utility  3.  Format the selected drive.  at this point,  the drive is no longer read-only.  however,  restoring the ipod to a usable partition table is beyond my level of skill.

---

