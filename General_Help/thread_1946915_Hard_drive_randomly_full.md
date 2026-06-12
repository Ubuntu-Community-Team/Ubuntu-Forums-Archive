---
title: "Hard drive randomly full"
date: 2012-03-25
forum: General Help
---

### Post by bobman321123 on 2012-03-25
I have two partitions on my 500GB hard drive.
One is 191gb for a windows partition, and the rest goes to ubuntu.
Two days ago, my ubuntu was filled up 23%, and today, it's at ~97%. I haven't downloaded anything significantly sized, what could possibly be going wrong? My windows partition also randomly filled up to near maximum even though I haven't booted to windows in weeks.
Help?

---

### Post by oldfred on 2012-03-25
That is a lot of space to fill.

Do you have any automatic tasks like backup running?

Are you getting some errors and the log files are going berserk?

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

This will only show mounted partiitons:
Partition sizes
df -Th | sort

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h

---

### Post by bobman321123 on 2012-03-25
After following the first two guides, the file systems are at 70% for windows, and 86% for Ubuntu. I can't seem to find any significant drain of space. (I mean sure I have 17 gb here and there for random things on my hard drive, but nothing that would randomly knock off 150 gb in two days.)

---

### Post by oldfred on 2012-03-25
Do you have any large files or large folders from commands given?

---

### Post by bobman321123 on 2012-03-26
```
sudo du -h --max-depth=1 / | grep '[0-9]G\>' # folders larger than 1GB
```
Tells me that my home folder somehow contains 200GB of files, but when I look through it, it doesn't say what it is.

When I run:
```
sudo find / -name '*' -size +1G # files larger than 1GB
``` I found several files, but nothing noteworthy.
I've deleted some of my files, and have my ubuntu partition down to 55%, but I'd still really like to know where that space went in the first place.

```
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
``` Gave me a list of folders and space usage, but I only have ~6 folders that are even over 1GB, for a total of about 50gb, which doesn't really explain where the other 100gb is going.
*sigh* all this after I fix my last computer issue. :P

---

### Post by pqwoerituytrueiwoq on 2012-03-26
i had a similar issue happen once on ubuntu 9.04 it is a issue with printer making the system go crazy with the log files i used [bleachbit]("apt:bleachbit") to get my space back
you may want to look in /var/log for any multi gig logs and delete them so you will have the pace to install bleachbit

---

### Post by bobman321123 on 2012-03-26
/var/log had no large files in it.
At least, I don't think so. I ran the command from the above post... ```
sudo find / -name '*' -size +1G # files larger than 1GB
```modified (I think) to search /var/log, like this.
```
sudo find /var/log -name '*' -size +1G # files larger than 1GB
```

---

### Post by oldfred on 2012-03-26
You said your /home was the issue. Then it should not be log files. Did you download any large files, or turn on show hidden files and see if something very large is in /home.

Or you can run commands in every folder in /home.

---

### Post by bobman321123 on 2012-03-26
I did a bit of downloading, but my internet isn't nearly good enough to knock out 100gb in 2 days (even if I were to try).

---

### Post by arclance on 2012-03-26
Try running this from /home or any directory you suspect of containing the files.
```
ls --recursive --all -Slh

```ls seems to find more files that the other commands you have been trying, but is not sorted as nicely.

Look through the results for large files or directories containing a very large number of files.
Don't assume that the files you are looking for are 1GB+ in size.
You may have a large number of files under 1GB that add up to the missing space on your drive which will not be listed by one of the commands you ran before.

I know this from experience.....
I once wrote a script that made about 40 GB of text files over two weeks due to an unknown function of calcurse.  
I reached the max number of files for a ext4 partition and it took 24 hours to delete them all after figuring out that the "out of space" error I was getting did not differentiate between "max number of files reached" and "no space left on drive".

---

### Post by bobman321123 on 2012-03-28
Yeah, I still haven't been able to figure out where the 100 gb went, but I'm down to a reasonable fill amount (55%, and it hasn't changed), so I think I'm going to just give up and mark this thread as solved. 
Thanks for all your suggestions, guys.

---

### Post by mogsareus on 2012-05-05
I have a similar problem
Attempt to up grade 10.10 on line fails after 3-1/2hrs - corrupt files, including boot.
Shut down screen script replaced with vertical rectangles.
Will not reboot.
Boot from 11.11 Canonical CD - need to upgrade to 11.04 first.
Try to upgrade to 11.04 on line, insufficient space on hard drive.
Hard drive analyzer says disc is 100% full. - Its a 500GB disc.
Tried clean and auto clean - nothing happens.
Tried  ls --recursive --all -Slh - lots files all showing todays date.

I would like to know what has happened here - but my level of experience is beginner.

---

### Post by jonnyboysmithy on 2012-05-05
I also had a similar problem. The way I dealt with it was to track it down to where it was. I knew the huge file was in my home folder. So I just selected half of the files in my home folder and checked how large it was. Check the propeties. It wasn't in this half so it must be in the other half of the selection. Then of that half I select half and check again which half holds the missing space. Continue till you track it down. Shouldn't take all that long.

---

### Post by mogsareus on 2012-05-07
Intending to follow the advice of johnyboysmithy I started the machine this evening, being under the impression it would need to boot from disc I pressed DEL to select boot from disc before remembering the correct key is Esc.
I also pressed the CD door button - it opened and then closed, pressing it again opened it allowing me to insert my 10.10 disc. 
Before the door fully closed the machine had booted up and asked for my log in information.
I then looked at Disk Analyzer again - it now shows Total file system capacity 450.9 gb, file usage 36.9gb.
The machine appears to be working normally.
I haven't check which version of Ubuntu I am on yet  - I'll check discs etc next.

---

