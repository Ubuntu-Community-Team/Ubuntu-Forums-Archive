---
title: "Simple Backup + grsync"
date: 2009-12-01
forum: General Help
---

### Post by GiganticDays on 2009-12-01
I'm a recent convert to Ubuntu and am currently using simple backup to backup my data and important directories. I would like to use grsync to sync the backup folder with one on an external hdd.
I keep running into file permission errors.

sbackup files are root-owned and have no user permissions so they simply don't get copied.

Is there any way to change this (or is that not advisable)? If not, what can I do to automate backups and copy the entire backup folder to the external hdd?

---

### Post by pbrane on 2009-12-01
You can probably run grsync in a terminal as root by typing **gksudo grsync**.
I use rsync directly and have written a script with all the parameters I need, including an exclude file.

I would not advise you to change the file/directory permissions as this may comprimise your system.

---

### Post by akakingess on 2009-12-01
> **pbrane said:**
> You can probably run grsync in a terminal as root by typing **gksudo grsync**.
I use rsync directly and have written a script with all the parameters I need, including an exclude file.

I would not advise you to change the file/directory permissions as this may comprimise your system.

Would it be possible to get you to share that script, I am just now reading a book on Bash Scripting so forgive if it's offensive to ask? However, I do agree with you that if permissions are set on a folder, they are set usually for reasons of system stability and changing them are usually not recommended.

---

### Post by GiganticDays on 2009-12-01
Thanks pbrane. That's running now.

---

### Post by pbrane on 2009-12-01
The script is a VERY simple script. It is used to sync my home directory, minus some excludes, to a flash drive. This script could be adapted to backup anything to anywhere though.

Have a look at this link:
[http://rsync.samba.org/examples.html]("http://rsync.samba.org/examples.html")

```

#!/bin/bash
# script to backup my home directory

# drive to backup to
DISK=/path/to/backup_drive

# exclude these files/directories
EXCLUDES=$HOME/path_to/exclude.txt

# option to rsync
OPTS="-avlt --stats --delete --exclude-from=$EXCLUDES"

# directory to backup
BDIR=$HOME

# do the actual transfer
rsync $OPTS $BDIR $DISK

```

---

### Post by akakingess on 2009-12-01
> **pbrane said:**
> The script is a VERY simple script. It is used to sync my home directory, minus some excludes, to a flash drive. This script could be adapted to backup anything to anywhere though.

Have a look at this link:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

```

#!/bin/bash
# script to backup my home directory

# drive to backup to
DISK=/path/to/backup_drive

# exclude these files/directories
EXCLUDES=$HOME/path_to/exclude.txt

# option to rsync
OPTS="-avlt --stats --delete --exclude-from=$EXCLUDES"

# directory to backup
BDIR=$HOME

# do the actual transfer
rsync $OPTS $BDIR $DISK

```

Thanks again pbrane (I almost feel bad calling you that ;) I will use it for exactly that purpose, just one question, does it include the hidden files? I am almost as concerned about those as my Docs and such. Just curious, either way, it is an excellent starting point and I appreciate you sharing!!!  I love this community...

---

### Post by chrisbay90 on 2009-12-01
> **akakingess said:**
> Thanks again pbrane (I almost feel bad calling you that ;) I will use it for exactly that purpose, just one question, does it include the hidden files? I am almost as concerned about those as my Docs and such. Just curious, either way, it is an excellent starting point and I appreciate you sharing!!!  I love this community...

Short answer. Yes.....maybe (whats in ~/path_to/exclude.txt?)
when given a directory rsync will sync EVERYTHING inside that folder. you can use the option --exclude to do as the name suggests. If you want to exclude a list of files/directories then you can supply rsync with a text file containing a list of things to exclude.

Thats exactly what this script does. So it will backup everything in your home folder (hidden files included) unless specifically listed as not to be copied in ~/path_to/exclude.txt

Note that ~/path_to/exclude.txt as well as most other parameters in that script are fictional examples for you to fill in as your need require.

```
01 #!/bin/bash
02 # script to backup my home directory
03 
04 # drive to backup to
05 DISK=/path/to/backup_drive
06 
07 # exclude these files/directories
08 EXCLUDES=$HOME/path_to/exclude.txt
09 
10 # option to rsync
11 OPTS="-avlt --stats --delete --exclude-from=$EXCLUDES"
12 
13 # directory to backup
14 BDIR=$HOME
15 
16 # do the actual transfer
17 rsync $OPTS $BDIR $DISK
```line 5: you MUST change this to the location you want your backups to be saved.
line 8: if you want to exlude anything make a list and put them in a text file then change this to point to that file.
line 11: you's probably want to leave it as is. If you dont want to exlude anything in your home folder then remove the last part  `--exclude-from=$EXCLUDES` especially if its value is `$HOME/path_to/exclude.txt` and that files doesnt exist.
Line 14 & 17: you'd probably want to leave these intact. **EDIT: based on pbrane's update make sure line 14 is BDIR=$HOME/ with the trailing slash.**

however simple nice script pbrane. Even though it is only 5 lines long I like its elegance.

---

### Post by pbrane on 2009-12-01
Like I said, this is a very simple script. Mostly written to avoid retyping the same thing on the command line over and over. And yes, chrisbay90 is correct, the script will backup everything in the $HOME directory, except whatever I put in the exclude file. Here are some things I don't backup:
```

.gvfs
download
.cache
Videos
*.o
.wapi
.thumbnails

```

Also on chrisbay90's post lines 5 and 8 need to be changed for your system. You don't have to use an exclude file, but some directories like .gvfs may not copy. And this may not work as a cron job without changing $HOME to the explicit path you intend to backup.

BTW:
[I]Gauge field strengths that are p+2-forms turn out to have sources that are p-dimensional objects. We call these p-branes.

A p-brane spacetime whose metric solves the equations of motion for a (p+2)-form field strength in d spacetime dimensions can be described using p space coordinates {yi} along the p-brane and (d-1-p) space coordinates {xa} orthogonal to the p-brane.[/I] 

Yeah I know, weird.

OOPS:

on line 14 should read **BDIR=$HOME/** You need to add the trailing slash.

---

### Post by chrisbay90 on 2009-12-01
> **pbrane said:**
> ...SNIP...
Also on chrisbay90's post lines 5 and 8 need to be changed for your system. You don't have to use an exclude file, but some directories like .gvfs may not copy. And this may not work as a cron job without changing $HOME to the explicit path you intend to backup.

BTW:
[I]Gauge field strengths that are p+2-forms turn out to have sources that are p-dimensional objects. We call these p-branes.

A p-brane spacetime whose metric solves the equations of motion for a (p+2)-form field strength in d spacetime dimensions can be described using p space coordinates {yi} along the p-brane and (d-1-p) space coordinates {xa} orthogonal to the p-brane.[/I] 

Yeah I know, weird.

OOPS:

on line 14 should read **BDIR=$HOME/** You need to add the trailing slash.

oops seem to have listed the line numbers wrong. Fixed now.

It is hard to make me laugh at maths at 1:38am. However here I am chuckling. Wierd yeah, but here i am now making a note to further my mathematical knowledge of p-branes tomorow.

---

### Post by akakingess on 2009-12-01
Thanks for the explanations, both of you, and I will be using this script (slightly modified of course) and especially thanks pbrane for the explanation on the name, makes me not feel so insignificant asking a "pea brain" for help : )

---

### Post by pbrane on 2009-12-01
You are welcome. It's probably debatable whether or not you asked a "pea-brane" for 
help though.

I find that using scripts to automate some tasks is very convienient. Trying to remember how I did something yesterday, much less last week, can be frustrating.

---

### Post by akakingess on 2009-12-01
Another quick question that I thought of, would running the script upon shutdown count as a cron job, or not, that would help with the $HOME issue as well, again, nothing that can't be changed, I just take every opportunity I can to learn and pick the brains of others..

---

### Post by chrisbay90 on 2009-12-01
> **akakingess said:**
> Another quick question that I thought of, would running the script upon shutdown count as a cron job, or not, that would help with the $HOME issue as well, again, nothing that can't be changed, I just take every opportunity I can to learn and pick the brains of others..

If you added it to your crontab file (`crontab -e` at the terminal than adding a line schedualing it) than yes thats a cronjob. A quick google or maybe even that book your reading should tell you all you need to know about cron.

How exactly would you be setting it to run at shutdown? Not that it matters greatly though. However if you ever change it to do an entire system backup i'd recomend you dont do it at shutdown as thats usually when updates are installed so you could be creating a snapshop of something potentially unstable. Should be fine just for backing up home.

What home issue? (Serious question)

---

### Post by akakingess on 2009-12-01
> **chrisbay90 said:**
> If you added it to your crontab file (`crontab -e` at the terminal than adding a line schedualing it) than yes thats a cronjob. A quick google or maybe even that book your reading should tell you all you need to know about cron.

How exactly would you be setting it to run at shutdown? Not that it matters greatly though. However if you ever change it to do an entire system backup i'd recomend you dont do it at shutdown as thats usually when updates are installed so you could be creating a snapshop of something potentially unstable. Should be fine just for backing up home.

What home issue? (Serious question)

In regards to the Home issue, on post # 8 from pbrane, he mentioned that the way the script was written (with $HOME) that it may not work with cron.  You are correct though, a simple look through the book I am just starting should answer all of my questions, and I should stop being lazy and making all of the experienced people answer questions I need to learn on my own :D.  I am definitely going to have to read up on cron though, as it is something I know will be useful for me and I know almost nothing about it at this time, but I do read and google and try as much as I can on my own, I just accidentally hijacked this thread to ask some of my own selfish questions.

---

### Post by chrisbay90 on 2009-12-01
> **akakingess said:**
> In regards to the Home issue, on post # 8 from pbrane, he mentioned that the way the script was written (with $HOME) that it may not work with cron.  You are correct though, a simple look through the book I am just starting should answer all of my questions, and I should stop being lazy and making all of the experienced people answer questions I need to learn on my own :D.  I am definitely going to have to read up on cron though, as it is something I know will be useful for me and I know almost nothing about it at this time, but I do read and google and try as much as I can on my own, I just accidentally hijacked this thread to ask some of my own selfish questions.

I think what pbrane is saying is that you should explicitly specify your home folder rather than useing the enviromental variable $HOME. In other words line 14 should read `BDIR=/home/your_usename/` where your_username is whatever your username is on that system.

Thats fine, im just glad i can help. So long as GiganticDays got the help he/she was looking for, than by all means ask away its the best way to learn.

---

### Post by akakingess on 2009-12-01
> **chrisbay90 said:**
> I think what pbrane is saying is that you should explicitly specify your home folder rather than useing the enviromental variable $HOME. In other words line 14 should read `BDIR=/home/your_usename/` where your_username is whatever your username is on that system.

Thats fine, im just glad i can help. So long as GiganticDays got the help he/she was looking for, than by all means ask away its the best way to learn.

I agree, the OPs issue was the most important, which is why I don't feel completely guilty about "hijacking" the thread, and when it comes to my true home path, I am advanced enough to get that far (well passed that for that matter), so thank you all for giving me the cheap/easy answers, as opposed to my waiting a week until I got to that page :p

Thanks to all of you for your collective help,

akaKingESS

---

### Post by pbrane on 2009-12-01
The problem using environment variables like **$HOME** is that if the script is run by another user (root) then **$HOME** expands to that users home directory. Also if you run the script during shutdown I would think that the script would also shutdown.

---

### Post by nikos_ on 2010-01-17
Hi, 

I have a problem with grsync too. I run grsync 0.9.2 on ubuntu 9.10. I back up my home/username folder onto an external HD (USB).

My aim is to simplify the backing up process for the contents of my home/username folder (this contains the Desktop, Documents, Music, Video etc folders). Thus, instead of recopying the entire home/username folder, or manually going and updating selectively the back up folder with the newly modified files, I want to grsync to handle the process and update the replicate (back up) folder on my external HD.

Grsync works, it seems to do the job, but it takes absolute ages! It takes about 30-40 minutes to complete the task, with the external HD's LED flickering, meaning that it either updates or re-copies a lot of files (even if I've only newly modified a couple of files!!). It also shows warning messages. The key observation is that grsync does not only handle the back up of the Desktop, Documents, Music, etc. folders, but files that I don't want it to take care of. Thus, when I run it, I see on the progress list of its command line window that it checks firefox and system files and files with weird names (?!). I do not understand as these files are not contained in my /home/username folder, but I presume they are settings and system files in the /home folder.

I have definitely specified the /home/username folder as the source folder.

Can somebody advise me how to prevent this from happening, and make grsync backup ONLY my  /home/username folder? (I guess tghat would also solve the problem why grsync takes so long).

The weird thing is that, on my destination (external HD) folder, only the  /home/username folder appears, as it should. So what does grsync does when it goes through all the setting/system files (presumably from my /home folder)?

Thank you
Nikos.

---

### Post by sgosnell on 2010-01-17
It's also backing up all the hidden folders, which may have lots of changed files.  You don't have "ignore existing" checked, do you?

---

### Post by garryknight on 2010-01-17
> **nikos_ said:**
> I see on the progress list of its command line window that it checks firefox and system files and files with weird names (?!).

Those files with weird names are probably the contents of your Firefox cache. If you tell grsync to sync a directory, it will sync all of the contents of that directory, including all subdirectories unless you tell it not to. If there is a subdirectory you don't want synced, you can go to Grsync's Advanced options tab and enter this in the Additional options box: --exclude="/full/path/to/directory"

Obviously you need to replace "/full/path/to/directory" with the actual path, and you only need the quotes if the path contains spaces in it.

If there is more than one directory that you don't want synced, you can create a file containing the full paths to those directories, one per line, then pass the name of that path to grsync using the --exclude-from parameter in the Additional options box. For example, I have a file ~/.grsync/data-excludes and it looks like this:

```

*~
*.bak
home/.mozilla/firefox/azflt7r4.default/Cache

```So my Additional options box contains this:
  --exclude-from=~/.grsync/data-excludes
This way I sync everything in my /data directory (which includes my Firefox directory, symlinked to from my home directory, but that's another story) with the exception of all files whose names end in "~" or ".bak" and everything in my Firefox cache.

---

### Post by nikos_ on 2010-01-17
> **sgosnell said:**
> It's also backing up all the hidden folders, which may have lots of changed files.  You don't have "ignore existing" checked, do you?

hi, and thank you for your response. you are right, it is the hidden files that grsync is backing up (I didnt know my home/username folder contained hidden files!). Thank you!

No, "ignore existing" is not checked. Should I have it checked? (what does this do, and how would it affect/solve my problem)?

Nikos

---

### Post by nikos_ on 2010-01-17
> **garryknight said:**
> Those files with weird names are probably the contents of your Firefox cache. If you tell grsync to sync a directory, it will sync all of the contents of that directory, including all subdirectories unless you tell it not to. If there is a subdirectory you don't want synced, you can go to Grsync's Advanced options tab and enter this in the Additional options box: --exclude="/full/path/to/directory"

Obviously you need to replace "/full/path/to/directory" with the actual path, and you only need the quotes if the path contains spaces in it.

If there is more than one directory that you don't want synced, you can create a file containing the full paths to those directories, one per line, then pass the name of that path to grsync using the --exclude-from parameter in the Additional options box. For example, I have a file ~/.grsync/data-excludes and it looks like this:

```

*~
*.bak
home/.mozilla/firefox/azflt7r4.default/Cache

```So my Additional options box contains this:
  --exclude-from=~/.grsync/data-excludes
This way I sync everything in my /data directory (which includes my Firefox directory, symlinked to from my home directory, but that's another story) with the exception of all files whose names end in "~" or ".bak" and everything in my Firefox cache.


Thank you so much for your thorough and explicit response. I will try your tip too, it makes perfect sense. Being new in Ubuntu, I just looked at the View > Show hidden files tickbox in the menu, and when I ticked it, I saw all the weird file grsync backs up. So I'll make the exclusion file you mentioned. Many thanks for your help!

I'm thinking, conversely, instead of telling grsync which folder to *exclude* from the home/username folder, which may vary as I install applications that create those settings files and so on, can I make a file that tells grsync which files to *include only *from my home/username folder? Thus, it would be easier to tell grsync to only back up the Documents and Music and Video folder (than list all the 'nonsense' to exclude). If so, could you please details how to do this? I am new, so the more details, again, the more helpful for me. Thank you for your time, I appreciate your input a lot.

Nikos

---

### Post by sgosnell on 2010-01-17
No, checking it will cause grsync to write over existing files, taking longer.  I think you might want to take note of garryknight's suggestion, and have grsync ignore files you don't need to keep, like firefox's cache and other temporary files.  These change constantly, so if they're included, they will all be copied, even if you think you haven't changed anything.

---

### Post by garryknight on 2010-01-18
Grsync is a graphical front-end to the rsync command so you can find out what other parameters you can put into the Additional options box by consulting the manual for rsync. For this you need to open a console (konsole on the Sytem menu in KDE, no idea what's available in Gnome, sorry) and enter the command 'man rsync' (without the quotes); when you've done reading and are suitably baffled, press Q to quit the manual. ;)

The manual page for rsync shows, amongst many others, the following command-line parameters:
            --include=PATTERN       don't exclude files matching PATTERN
            --include-from=FILE     read include patterns from FILE
            --files-from=FILE       read list of source-file names from FILE

I haven't used any of these, but my guess is that the middle one would do what you want. I suggest you try it and report back if you have any problems.

---

### Post by nikos_ on 2010-01-20
> **garryknight said:**
> Grsync is a graphical front-end to the rsync command so you can find out what other parameters you can put into the Additional options box by consulting the manual for rsync. For this you need to open a console (konsole on the Sytem menu in KDE, no idea what's available in Gnome, sorry) and enter the command 'man rsync' (without the quotes); when you've done reading and are suitably baffled, press Q to quit the manual. ;)

The manual page for rsync shows, amongst many others, the following command-line parameters:
            --include=PATTERN       don't exclude files matching PATTERN
            --include-from=FILE     read include patterns from FILE
            --files-from=FILE       read list of source-file names from FILE

I haven't used any of these, but my guess is that the middle one would do what you want. I suggest you try it and report back if you have any problems.

> and are suitably baffled
That would not take too long to happen!

This is extremely helpful, I will try at some point and get back to this thread. Thank you!
Nikos.

---

### Post by nikos_ on 2010-01-21
> **garryknight said:**
> Grsync is a graphical front-end to the rsync command so you can find out what other parameters you can put into the Additional options box by consulting the manual for rsync. For this you need to open a console (konsole on the Sytem menu in KDE, no idea what's available in Gnome, sorry) and enter the command 'man rsync' (without the quotes); when you've done reading and are suitably baffled, press Q to quit the manual. ;)

The manual page for rsync shows, amongst many others, the following command-line parameters:
            --include=PATTERN       don't exclude files matching PATTERN
            --include-from=FILE     read include patterns from FILE
            --files-from=FILE       read list of source-file names from FILE

I haven't used any of these, but my guess is that the middle one would do what you want. I suggest you try it and report back if you have any problems.


That's great. I opened Terminal, typed man rsync, and found what you said (pasting below):

            --exclude=PATTERN       exclude files matching PATTERN
            --exclude-from=FILE     read exclude patterns from FILE
            --include=PATTERN       don't exclude files matching PATTERN
            --include-from=FILE     read include patterns from FILE
            --files-from=FILE       read list of source-file names from FILE

Note the last one, which basically allows you to simply specify the source files.

Thus, in the Advanced options of grsync, I typed:
--files-from=/home/username/grsyncfiles.txt

where grsyncfiles.txt is a simple file where I wrote:

/Desktop
/Documents
/Downloads
/Music
/Pictures
/Songbird
/Videos

Note that these relative references where sufficient, as in the main page of grsync I had already specified as source folder the /home/username directory
and, therefore, anything specified in my txt file follows that specification.

Thus, as I use the FILE command in the Advanced option, this will only back up the specified files, thus leaving out the hidden ones that I wanted to disregard in the first place.

It works great now! Thanks again for your advice.
Nikos.

---

### Post by garryknight on 2010-01-22
You're very welcome.

---

