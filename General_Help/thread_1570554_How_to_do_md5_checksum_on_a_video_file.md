---
title: "How to do md5 checksum on a video file"
date: 2010-09-08
forum: General Help
---

### Post by Jenga-kun on 2010-09-08
I've got a few video files that came with md5's. I want to check them but I don't know how. Can someone help?

---

### Post by amauk on 2010-09-08
md5sum /path/to/file

---

### Post by undecim on 2010-09-08
1. open a terminal

2. type "cd folder" where folder is the folder the videos are in, e.g. "Videos", "Desktop", etc. (remember that this is case sensitive. If they are in your home directory, just skip this step completely.)

3. type "md5sum *.avi" to sum all .avi files in the directory. (if they are another file extension, replace avi with that extension). You can also check individual files with "md5sum filename"

---

### Post by Jenga-kun on 2010-09-08
> **undecim said:**
> 1. open a terminal

2. type "cd folder" where folder is the folder the videos are in, e.g. "Videos", "Desktop", etc. (remember that this is case sensitive. If they are in your home directory, just skip this step completely.)

3. type "md5sum *.avi" to sum all .avi files in the directory. (if they are another file extension, replace avi with that extension). You can also check individual files with "md5sum filename"

Ok, in terminal I'm putting in:

cd /media/2nd HD

and I'm getting:

bash: cd: /media/2nd: No such file or directory

---

### Post by Nytram on 2010-09-08
When filenames have a space in them it's necessary to enlose them in speech marks:

**cd "/media/2nd HD"**

---

### Post by inameiname on 2010-09-08
Here's a very easy to use script to do this. Just add inside your '~/.gnome2/nautilus-scripts' folder. Then just right click the file, or files, and it'll show you the checksums.

[http://gnome-look.org/content/show.php/Cooleech%27s+Hash+Checker+improved?content=129508]("http://gnome-look.org/content/show.php/Cooleech%27s+Hash+Checker+improved?content=129508")

---

### Post by Jenga-kun on 2010-09-08
> **Nytram said:**
> When filenames have a space in them it's necessary to enlose them in speech marks:

**cd "/media/2nd HD"**

Thanks, that worked.

[QUOTE=inameiname]Here's a very easy to use script to do this. Just add inside your '~/.gnome2/nautilus-scripts' folder. Then just right click the file, or files, and it'll show you the checksums.

[http://gnome-look.org/content/show.p...content=129508](http://gnome-look.org/content/show.p...content=129508)[/QUOTE]

Thanks, I'll set that up first chance I get.

---

