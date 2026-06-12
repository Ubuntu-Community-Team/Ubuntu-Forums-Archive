---
title: "command to remove spaces from filenames?"
date: 2010-08-18
forum: General Help
---

### Post by x-shaney-x on 2010-08-18
I have just switched to banshee as my media player and imported my films and music.
Problem is, the video list is quite hard to read because all the video files have spaces in their names which are replaced by % signs, numbers and letters.
I'm wondering if there is a command I can use in the directory that will automatically remove all the spaces from the filenames or better still, replace the spaces with hyphens or underscores?

---

### Post by inameiname on 2010-08-18
Using this python script, you could open the folder and by selecting all filenames, it will remove whatever you desire, such as spaces.

For your specific problem, you can use the 'substitute' option with that script (which you add to your /home/(your username)/.gnome2/nautilus-scripts folder and the select all the highlighted files) and replace the what I'm guessing is '%20' to '-' and voila. There's even a handy preview option in the script to show what the files will look like before you change anything.

---

### Post by blur xc on 2010-08-18
> **x-shaney-x said:**
> I have just switched to banshee as my media player and imported my films and music.
Problem is, the video list is quite hard to read because all the video files have spaces in their names which are replaced by % signs, numbers and letters.
I'm wondering if there is a command I can use in the directory that will automatically remove all the spaces from the filenames or better still, replace the spaces with hyphens or underscores?

To rename all fines in the current directory:
```
rename 's/\ /_/g' *
```

To recursively rename all files in the current directory and subdirectories
```
find . -type f -exec rename 's/\ /_/g' '{}' \;
```

I'm 99% certain that's right- you can try rename w/ the -n option to preview the new names before writing them.  I tested them in the terminal and they worked on my system.

Now, to also rename directories, that got a bit goofy, and I'm not invested enough in it to try and fix it right now.  I kinda half worked - it seems it renames the directory before renaming the files, but it looks for the files by the old directory name, and gives a no such file or directory error.  Running it twice completed the task (in my test, only one sub-dir), if there are more sub directories, it's probably need to be run more times.
```
find . -exec rename 's/\ /_/g' '{}' \;
```

It'd probably be safest to run it once w/ the -type f to rename all files, and again with -type d to rename all directories- I dunno...

Have fun.
BM

---

### Post by x-shaney-x on 2010-08-18
@ inameiname
I couldn't work out how to run the script as a nautilus script.
It appears in the right-click menu but does nothing on any file.
Presumably I need to run the script with a parameter but I have never used nautilus scripts so it's bit beyond me at the moment.
I'll look into it further since being able to run it from nautilus would be a better long-term way of doing it.

@ blur xc
Haven't tried the directory renaming but it worked perfectly on all the particular files I wanted the spaces removing.
Many ta's.

---

### Post by inameiname on 2010-08-18
Oh, my bad. I completely forgot that this particular script requires more than just the one piece of script. There are two files to copy and paste. Sorry about that.

Here is the actual webpage about it. I love this script for all sorts of things, especially as there isn't a built-in renamer for multiple files in Ubuntu. 

[http://gnome-look.org/content/show.php/Renamer?content=87601](http://gnome-look.org/content/show.php/Renamer?content=87601)

---

### Post by x-shaney-x on 2010-08-19
Wonderful. thanks.

---

### Post by inameiname on 2010-08-19
Sure. :)

---

