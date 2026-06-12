---
title: "Creating a shortcut"
date: 2010-06-24
forum: General Help
---

### Post by gabe17 on 2010-06-24
Hi! I want to do something like shortcut, that means: I will have an icon on my panel (or somewhere in menu, it isn't actually important where) and by clicking on this shortcut or icon, it would run some commands in command line. 
```

cd /
sudo su
tar cvpjf backup-home.tar.bz2 --exclude=/home/sth1 --exclude=/home/sth2 --exclude=/home/sth3 -exclude=/home/sth4  /home/ && tar -tvjf backup-home.tar.bz2 > backup-home.index.txt && split -a 1 -d -b 4300M backup-home.tar.bz2 backup-home.tar.bz2.part
tar cvpjf backup-system.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/backup-system.tar.bz2 --exclude=/backup-home.tar.bz2 --exclude=/backup-music.tar.bz2  --exclude=/home / && tar -tvjf backup-system.tar.bz2 > backup-system.index.txt

```

That means following: 
1. It runs comprimation of my home folder, exclude some folders
2. If the first task is done successfully, it runs the second task...
3. If the second task is done, it runs the third task,...
and so on...
 
So I want to do a shortcut that would do all these tasks for me automatically, I would only click on the icon and type my password (because of sudo su).

So I think I should save this "script" into .sh file, create an icon and link to this file. I've done this, but no success. Should I do something else? Thx.

---

### Post by Zolbad on 2010-06-24
I'm not entirely sure what you want to do. But couldn't you just save that script into a *.sh *file then to go properties and check "Run As Executable" Then apply and every time you would like to use it double click on the* .sh* file and then click run with terminal...

---

### Post by mooreted on 2010-06-24
Or make your script executable and right-click the panel, click add launcher and point to your script.

You can make a shortcut to anything.

---

### Post by Stilgar on 2010-06-24
> **gabe17 said:**
> Hi! I want to do something like shortcut, that means: I will have an icon on my panel (or somewhere in menu, it isn't actually important where) and by clicking on this shortcut or icon, it would run some commands in command line. 
```

cd /
sudo su
tar cvpjf backup-home.tar.bz2 --exclude=/home/sth1 --exclude=/home/sth2 --exclude=/home/sth3 -exclude=/home/sth4  /home/ && tar -tvjf backup-home.tar.bz2 > backup-home.index.txt && split -a 1 -d -b 4300M backup-home.tar.bz2 backup-home.tar.bz2.part
tar cvpjf backup-system.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/backup-system.tar.bz2 --exclude=/backup-home.tar.bz2 --exclude=/backup-music.tar.bz2  --exclude=/home / && tar -tvjf backup-system.tar.bz2 > backup-system.index.txt

```

That means following: 
1. It runs comprimation of my home folder, exclude some folders
2. If the first task is done successfully, it runs the second task...
3. If the second task is done, it runs the third task,...
and so on...
 
So I want to do a shortcut that would do all these tasks for me automatically, I would only click on the icon and type my password (because of sudo su).

So I think I should save this "script" into .sh file, create an icon and link to this file. I've done this, but no success. Should I do something else? Thx.

As the others have said you should create a file somewhere and call it backup.sh or whatever. At the beginning of the file put:

```
#!/bin/bash
```

And then put your code.

Now right-click on your desktop and select "Create Launcher". I think you've probably tried this and haven't had much success because your script is starts with "sudo su". What's happening is when you click the launcher, the script starts and then prompts for a password, but you aren't seeing the password prompt so nothing happens. 

Probably the best thing to do would be to remove the "sudo su" from the script, and have the launcher say something like "sudo /path/to/script/backup.sh". And when you create the launcher, drop down the "Type" box that says "Application" and set it to "Application in Terminal". This way you'll see a prompt for the password and you can enter it and allow the script to run.

As an alternative, you can have the launcher run something like "gksudo /path/to/script/backup.sh" which will open a window which will prompt for a password. Then you won't have to set as "Application in Terminal", and just have it as an "Application", although having just as Application means you won't see the out put of your script.

Oh and BTW, if you're making some backup scripts you might want to check out rdiff-backup. It makes incremental backups painless and once you've done the first backup, all future backups take almost no time at all.

---

### Post by guyshoxton on 2010-06-24
I didnt understand your question but...

To add a folder to the panel, open your home folder and drag it to your panel (for example Documents or Pictures)

to add it to your desktop you right click on the folder > Make link .. then you drag that to your desktop =)

---

### Post by gabe17 on 2010-06-25
Stilgar: That's exactly what I wanted. I haven't tried it yet, but I will. And what about the rndiff-backup, it looks very good, but I don't know how to work with it. I've read the man page, but it's too complicated for me. I need the rndiff-backup to do exactly what I've written in my first post:```
cd /
sudo su
tar cvpjf backup-home.tar.bz2 --exclude=/home/sth1 --exclude=/home/sth2 --exclude=/home/sth3 -exclude=/home/sth4  /home/ && tar -tvjf backup-home.tar.bz2 > backup-home.index.txt && split -a 1 -d -b 4300M backup-home.tar.bz2 backup-home.tar.bz2.part
tar cvpjf backup-system.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/backup-system.tar.bz2 --exclude=/backup-home.tar.bz2 --exclude=/backup-music.tar.bz2  --exclude=/home / && tar -tvjf backup-system.tar.bz2 > backup-system.index.txt
```Could you write me a command for rndiff to do this? Thx.

---

### Post by Stilgar on 2010-06-28
sorry for not getting back to ya... been busy with stuff.

Now there are advantages and disadvantages to rdiff-backup. You're obviously burning your backups to DVDs, in which case what you're doing now is the best method for that. rdiff-backup is better if you're backing up your files to an external USB drive or to another computer. The backup method you're using compresses the backup so thats another advantage of using tar. 

The advantage of rdiff-backup is that it backs up the changes to the files. The first backup you do with rdiff-backup may take hours. But after that first backup your backups will only take a few minutes. And it doesn't remove any of the old files. So if you delete a file and then run a backup, you will still be able to restore the file you deleted.

To backup your files there are a couple of ways to do it. The short answer is (I think):

```
rdiff-backup --exclude-special-files --exclude=/home/sth1 --exclude=/home/sth2 --exclude=/home/sth3 --exclude=/home/sth4  /home/ /backup/destination 
```


The longer answer is you can do something like this:

```
/usr/bin/rdiff-backup  --exclude-special-files --exclude-globbing-filelist=rdiff-home-exclude / /backup/destination
```

then create a text file called "rdiff-home-exclude" and put in the following:

```
/home/sth1
/home/sth2
/home/sth3
/home/sth4
**/lost+found
**.tar.bz2
**/backup-ignore
**/oldmusic/*.mp3

```

this would backup all the files in home except sth1, sth2, etc. It would ignore lost+found, ignore any files with the tar.bz2 extension, and ignore any directory called "backup-ignore" no matter where in the directory tree it is. It will ignore .mp3 files if they are in a directory called "oldmusic" but will backup all the other mp3s.

Its pretty powerful, and in my opinion easier than tar.

But like I said before, if you're putting you're backups onto DVDs then rdiff-backup isn't going to do that as well as tar. I suppose you can backup to usb with rdiff-backup and then tar that up now and then to burn it to a dvd.

---

### Post by gabe17 on 2010-06-29
Thanks very much for help. I have been burning the backup tars to DVDs so I have been using tar, but I will buy an extern hard drive and try the rndiff then. I will let you know if I succeed.

---

### Post by gabe17 on 2010-06-29
I've already bought a new external drive, so going to try the rndiff. But one question, where should be the file placed? In the directory where running the command, or is there a speacial place where it should be placed?

---

### Post by gabe17 on 2010-07-02
rdiff-backup works, but what is wrong in this? 

The "shortcut" command:

```
sudo /home/user/Ubuntu/backup.sh
```

The backup.sh file: 

```
#!/bin/bash
cd Ubuntu
rdiff-backup  --exclude-special-files --exclude-globbing-filelist=rdiff-exclude / /media/extern_HDD/
```

---

### Post by Stilgar on 2010-07-04
it looks good. Though you don't need the "cd Ubuntu" at the beginning.

if you just enter "sudo /home/user/Ubuntu/backup.sh" in a terminal, does it give any output?

You may want to check to make sure backup.sh is executable.

---

### Post by J V on 2010-07-04
You wouldn't need a script for this...

```
cd / && gksudo tar cvpjf backup-home.tar.bz2 --exclude=/home/sth1 --exclude=/home/sth2 --exclude=/home/sth3 -exclude=/home/sth4  /home/ && gksudo tar -tvjf backup-home.tar.bz2 > backup-home.index.txt && gksudo split -a 1 -d -b 4300M backup-home.tar.bz2 backup-home.tar.bz2.part && gksudo tar cvpjf backup-system.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/backup-system.tar.bz2 --exclude=/backup-home.tar.bz2 --exclude=/backup-music.tar.bz2  --exclude=/home / && gksudo tar -tvjf backup-system.tar.bz2 > backup-system.index.txt
```&& by default only runs a command if the last one was successfull, you can have this all on one line like so... gives a nice graphical sudo too. Adapt the other script and no files needed

---

### Post by gabe17 on 2010-07-05
Yes, Stilgar, you were right. The file wasn't executable. Now it works. Thanks everybody who posted for help! 
// The thread can be locked, problem SOLVED

---

