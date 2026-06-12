---
title: "Some newbie problems"
date: 2006-02-19
forum: General Help
---

### Post by hojgaard on 2006-02-19
Hey there...
I have been using linux/ubuntu for some months now, and i like it... I have met som problems but it always seems to be able to fix. But i have some questions i would like you to answer. 

1. In windows there is exe files in every program so if its not in start>programs you can allways find an executeble in the Program Files. But i can't find a replacement for the exe files, or at least a way to open programs which is not in the on the desktop and in "Programs"

2. I have just installed some themes and i found out that Metacity is good for that, so i wanted to use that. I found it in synaptic but how do i use it. i cant find it in "Programs"...

Maybe i'll come up with more....

---

### Post by christhemonkey on 2006-02-19
```
/usr/bin/
```
is full of programs!

And metacity comes preinstalled with ubuntu?
It is the default window manager...

---

### Post by jrib on 2006-02-19
1.  Linux doesn't really use file extensions, it uses information from the file itself to figure out if it is a movie, text file, or something else.  A file is made executable by giving it executable permissions.  So you could run an sh script by doing 'sh scriptfile'.  That will call the sh program with scriptfile as an argument ('sh /path/to/scriptfile') and sh will go and run what it reads in.  Or, since sh scripts generally  have headers that point to the sh program, you can just make it executable ('chmod +x /path/to/script_file') and then run it directly. '/path/to/script_file'

Some packages don't give you a menu item.  This usually happens when the program is command line based.  Usually, you can go to 'applications menu > accessories > terminal' and just type the name of the program since they tend to get named that way.  But to find out all of the files that a program installs to 'bin' folders, you can do ```
dpkg -L packagename| grep bin
```.  The first part there lists package contents and the grep filters for only instances of 'bin'.  That should allow you to determine the proper way to run your program.

2.  Just download a theme from a place like art.gnome.org or gnome-look.org.  When you do, it should have a tar.gz extension.  All you have to do is open 'system > preferences > themes', drag and drop the file into the window, and install it.  Then you should be able to use it.  If it is just a metacity theme, then you go to theme details and it should be in the 'window border' section.

---

