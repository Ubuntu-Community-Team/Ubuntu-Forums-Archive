---
title: "files disappeared"
date: 2009-09-02
forum: General Help
---

### Post by vashwood on 2009-09-02
I was about 20gb of files to my external hard drive overnight, and when I woke up this morning the entire folder on my system was empty.  I had about 200gb of files in that folder.  It was a folder in my /home that was on a separate partition.

What I tried doing so far is unmoutning that partition and running fsck, but the files are still missing.  It looks like the space is still taken up but the files just dont show up.

Does anyone have any ideas?  It was a ext3 filesystem.

---

### Post by Finalfantasykid on 2009-09-02
Maybe try doing a disk usage analyzer on that drive.

Applications > Accessories > Disk Usage Analyzer

It should be able to locate where all the files are located, maybe it just went to somewhere else on the disk for some strange reason.

---

### Post by listener on 2009-09-02
A mistake in changing permissions for files can cause them to seem to disappear.  Just a thought.  It is because you are not allowed to even know they exist, I think even as root.  If this is what happened, setting the permissions correctly will resolve the problem.  

Good Luck

Bob

---

### Post by Bucky Ball on 2009-09-02
If you know the exact name of any of the files, you could look in a terminal by:

locate name_of_your_file, 

For instance, if the file name is Donkey, then

locate Donkey

... and see if anything shows up. That might give you a clue as to where they've gone.

---

### Post by vashwood on 2009-09-02
Thanks. I did a 'locate' and it points to the directory where the files 'should' be.  But again it doesn't show up in there :confused:

I also opened Nautilus as a root and under permissions, the folder is set to my userid

---

### Post by Bucky Ball on 2009-09-02
Weird. Try in a terminal:

sudo nautilus

This will open a file browser as root. Navigate to the appropriate folder and see if they are there. Maybe even 'view hidden files' if they're not ...

---

### Post by vashwood on 2009-09-02
I did a sudo nautilus and even 'show hidden files'. Nothing...

---

### Post by vashwood on 2009-09-02
whats the difference between 'find' and 'locate'? 

'Find' doesn't find the files at all

---

### Post by Vaphell on 2009-09-02
afaik locate uses database updated daily for fast access thus latest changes are often missing, find works in real time

---

### Post by vashwood on 2009-09-02
Thanks. I guess I'll try running Foremost and see if I can recover the files.

---

### Post by Vaphell on 2009-09-02
btw in such cases using GUI is less reliable than ls in command line, who needs that buggy nautilus :-)

good luck

---

### Post by Anxious Nut on 2009-09-02
try in terminal

```
cp -r Path_of_the_folder_that_contains_the_files ~/
```

use locate to get the path

---

### Post by Bucky Ball on 2009-09-02
> **Vaphell said:**
> using GUI is less reliable than ls in command line, who needs that buggy nautilus :-)


You should qualify that by saying who need buggy GUIs, the terminal is more reliable. But not everyone (especially newcomers) wants to use a terminal when they can do it with their mouse! Nautilus is indeed quick and easy for some stuff, not so good for others and I've never had a 'buggy' problem with it. 

Unfortunately, not everyone is addicted to the terminal. Do you even run a desktop?

ps: good idea AnxiousNut.

---

### Post by Vaphell on 2009-09-02
yes, in fact I do run a desktop and I know newcomers are afraid of terminal. In fact I am not an advanced user, but I learned that in serious cases command line works best, even for newcomers. It was just a semi-serious sentence.

If ls shows that stuff is there, it's there and you can relax. If not, you are SOL. It's fast and foolproof method to diagnose the problem.
Gui applications are not to be trusted in bad situations, they have various bugs and quirks that can somehow make files invisible  - I've read few threads about files disappearing from desktop and reportedly it was nautilus fault.

---

### Post by Anxious Nut on 2009-09-03
hey dude, before you use locate update your data base
```
sudo updatedb
```
then use locate, cuz it might be outdated and the files are really gone(i hope not) 

good luck

---

### Post by vashwood on 2009-09-03
> **Anxious Nut said:**
> try in terminal

```
cp -r Path_of_the_folder_that_contains_the_files ~/
```

use locate to get the path

I get this..

cp -r /home/user/Downloads/ ~/
cp: `/home/user/Downloads/' and `/home/user/Downloads' are the same file

---

### Post by vashwood on 2009-09-03
> **Anxious Nut said:**
> hey dude, before you use locate update your data base
```
sudo updatedb
```
then use locate, cuz it might be outdated and the files are really gone(i hope not) 

good luck

After updating the database, it doesn't find the files anymore.  I know the files are taking up the space still.

Is there anyway to recover the directory structure, including filenames?

---

### Post by todak on 2009-09-03
Try booting with a LiveCD and see if you can navigate to your files.

---

### Post by vashwood on 2009-09-03
Thanks, but Live cd didnt work either. I guess all is lost.  I mean all the space is still taken up, I just can't see the files.

Anyone have any recommendations on file recovery procedures? I just tried the method described on this site but it didn't fix the problem.

[http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html](http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html)

---

