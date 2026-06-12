---
title: "Checking for duplicate file names"
date: 2006-04-24
forum: General Help
---

### Post by dotancohen on 2006-04-24
I have some tens of recursive folders of pictures that I will move into one big folder. I want to be sure that there are no duplicate file names. Is there a program that will check if there are duplicate file names in a directory structure?

Thanks, all.

---

### Post by gingermark on 2006-04-24
[QUOTE=dotancohen]I have some tens of recursive folders of pictures that I will move into one big folder. I want to be sure that there are no duplicate file names. Is there a program that will check if there are duplicate file names in a directory structure?

Thanks, all.[/QUOTE]
Yes, [Komparator](http://www.kde-apps.org/content/show.php?content=33545)!
Follow that link, click "Ubuntu Download", and type ```
sudo dpkg -i komparator-0.3_i386.deb
``` to install!

---

### Post by dotancohen on 2006-04-24
Thanks, Gingermark. But Kompactor is for syncronizing two folders- not quite what I am doing. Before I move files from many folders to one big folder, I want to be sure that there are no duplicate file names. Kompactor won't do that.

A friend had suggested to me that I script it, but I know nothing about bash. If I think back to C classes in the university I figure that I would need to store the file name of each file in an array and then check for duplicates. How difficult is that to do in bash? I'm in no shape to do that in C nowadays. I'm not so certain that I would get Hello World out properly...

---

### Post by xenmax on 2006-04-24
Wont ```
mv -i source destination
``` work? It will prompt you before moving if another file with exact same name already exists. Test it out on a dummy file if you feel comfortable that way.

if you really want to script it to find out what files there are which share same names, i came up with this: its not a clean solution really, some others might be able to suggest better ways. Anyway,
```
find . -name "*.jpg" -exec basename '{}' \; | sort > full
find . -name "*.jpg" -exec basename '{}' \; | sort | uniq > uql
comm -3 full uql
``` Run this from base folder you have pictures in. [or change the '.' to path to that]
The first line is command that will output to a file name full (change full to something else if you have a file called full already) all jpg files found under '.' 
Same goes for second line [again, if file called uql already exists, change it], but this contains only unique file names
The third is what you want - a list of file names that repeat. But it has its short comings - it does not tell you exactly where those duplicates are: but you can run a find on those names[not practical if you have large number of duplicates - if that is the case, let me know and i will see if can improve it]

Hope this helps.

---

### Post by dotancohen on 2006-04-24
Wow, thanks, that was simpler than I thought it would be (most things in linux seem to be). I've got to go make the wife feel that she's not being ignored, so I will run this in a little while, but I really wanted to express my gratitude right now.

You guys are great.

---

### Post by gingermark on 2006-04-24
[QUOTE=dotancohen]Thanks, Gingermark. But Kompactor is for syncronizing two folders- not quite what I am doing. Before I move files from many folders to one big folder, I want to be sure that there are no duplicate file names. Kompactor won't do that.[/QUOTE]

Komparator will show you duplicate files in two directories, and if you turn of the md5 sum check, and the size comparison, it would then do what you wanted. EDIT: Although not from many directories at the same time - I see, sorry.

But fair enough, glad you got it sorted.

---

