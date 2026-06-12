---
title: "backups with tar for (full, Incremental, differential)"
date: 2009-07-30
forum: General Help
---

### Post by e24ohm on 2009-07-30
Folks:
How do I use tar and create backups that are Full, Incremental, and differential? Is this possible with tar, or should i use another command?

Currently I am using tar for massive folders; however, if possible I want to run incremental backups M, T and differentials on W, Thurs. and Full on Friday.

how do i do this from the cli, and use tar or another problem?

thank you,
e

---

### Post by e24ohm on 2009-07-30
I have found new resources, and a few are recommending "rsync"; however, i am not sure. can anyone offer suggestions?

---

### Post by mrog on 2009-07-30
You could try backupninja (for configurating)

[https://labs.riseup.net/code/projects/show/backupninja/](https://labs.riseup.net/code/projects/show/backupninja/)

which requires rdiff-backup

[http://rdiff-backup.nongnu.org/](http://rdiff-backup.nongnu.org/)

---

### Post by PGScooter on 2009-07-30
rsync is a great tool and can do what you want. It will take some reading on your part. The man page ```
man rsync
``` is full of information and there are a lot of tutorials. It is only command line, I believe, but that makes scheduling easier. As for scheduling, look into anacron.

---

### Post by e24ohm on 2009-07-30
> **PGScooter said:**
> rsync is a great tool and can do what you want. It will take some reading on your part. The man page ```
man rsync
``` is full of information and there are a lot of tutorials. It is only command line, I believe, but that makes scheduling easier. As for scheduling, look into anacron.thanks.

---

### Post by e24ohm on 2009-07-30
> **PGScooter said:**
> rsync is a great tool and can do what you want. It will take some reading on your part. The man page ```
man rsync
``` is full of information and there are a lot of tutorials. It is only command line, I believe, but that makes scheduling easier. As for scheduling, look into anacron.ok i have read through the manual, and saw the section for copying files, then update the files by sending only the difference; however, would I use tar then on the destination computer to archive the data into one file, then use gzip to compress?

---

### Post by PGScooter on 2009-07-31
> **e24ohm said:**
> ok i have read through the manual, and saw the section for copying files, then update the files by sending only the difference; however, would I use tar then on the destination computer to archive the data into one file, then use gzip to compress?

e240hm,

hmm great question! I think that would work, but if that's what you want to do then I don't know if rsync is the best option for you. The feature that sends only the difference is meant to save time and if you want to use gzip to compress and decompress then it might be quicker to just tar everything and replace the old tar. I'm not sure. Maybe you should search for a different program?

Is space an important issue?

It would be nice if rsync had the ability to do what you want automatically (sync a folder to a tar).

---

### Post by scouser73 on 2009-07-31
Have you tried [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), perhaps it's worth a look.

---

### Post by e24ohm on 2009-07-31
> **PGScooter said:**
> e240hm,

hmm great question! I think that would work, but if that's what you want to do then I don't know if rsync is the best option for you. The feature that sends only the difference is meant to save time and if you want to use gzip to compress and decompress then it might be quicker to just tar everything and replace the old tar. I'm not sure. Maybe you should search for a different program?

Is space an important issue?

It would be nice if rsync had the ability to do what you want automatically (sync a folder to a tar).I have a client that has a great deal of Flac and video archives. The budget has place a limit on resources, which i can accomplish a nice backup solution.

Space is a issue, along with the time it take for a backup to complete; however, we are talking about 160 GB worth of data, so I really do not want to backup the full 160 GB on a daily bases, since I am use older DDS tapes at this location. I know I should upgrade this client to LTO; however, the budget does not allow for that, so I am working with that I have for the client.

My solution was to use rsync to the server that has the tape drive. On this server I have a script running, which creates a folder, with the current date, so when I rsync the files over, the files are in the folder for the day of the week; however, I want to .tar the files into the archive format, and possibly compress to save even more space, with the goal to append to media. At this point, not sure if this is possible, but it is just an extra thought to get more space out of the tapes for them. Not really worried about spanning tapes right now, since the current data trend will not exceed past what is currently in place.

I have been reading about Backula; however, I am only starting to learn the server, and do not feel strong enough yet to deploy to a client.

thank you.
E

---

### Post by e24ohm on 2009-07-31
> **scouser73 said:**
> Have you tried [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), perhaps it's worth a look.wow i like the gui interface and thank you for speaking about this application; however, I am going to research this app a little more. I need the ability to archive to tape, which I in the screen shots, you can select a target, other then the CD/DVD. Also I need the ability to use the app with Cron.
      Thanks again for mention this program...now you have me another reason why not to answer my phone this morning, as I perform a little R&D.

Thanks.
E

---

### Post by matey3 on 2009-07-31
rsync works great but sometimes I get a time-out error?!
this is a good little script if you want to backup to another place or move it later:

 #!/bin/sh
   tar czvf $1.$(date +%Y%m%d-%H%M%S).tgz $1
   exit $?

of course you can take the minutes and seconds out, they are useful tho if you want to delete the older ones, 
save this like in a files called backit and then chmod 777 to ti then ./backit /etc or /bin or whatever directory you want to backup using tar.

for rsync you can do;

rsync -avz -e ssh ToMyServer(IP/Name):/directory/directory/ /toLocal/Directory/

you can do --progress or --delete-after (do this one with --dry-run first to make sure). -r or --recursive will do all sub-directories as well.

BTW the folders like /dev /sys /proc etc, should be excluded I think?
someone should shed some light on this subject.
thanks

---

### Post by e24ohm on 2009-07-31
> **matey3 said:**
> rsync works great but sometimes I get a time-out error?!
this is a good little script if you want to backup to another place or move it later:

 #!/bin/sh
   tar czvf $1.$(date +%Y%m%d-%H%M%S).tgz $1
   exit $?

of course you can take the minutes and seconds out, they are useful tho if you want to delete the older ones, 
save this like in a files called backit and then chmod 777 to ti then ./backit /etc or /bin or whatever directory you want to backup using tar.

for rsync you can do;

rsync -avz -e ssh ToMyServer(IP/Name):/directory/directory/ /toLocal/Directory/

you can do --progress or --delete-after (do this one with --dry-run first to make sure). -r or --recursive will do all sub-directories as well.

BTW the folders like /dev /sys /proc etc, should be excluded I think?
someone should shed some light on this subject.
thanks hey this is very similar to the script i run; however, I noticed when I included the "%H%M%S" for the hour, minute, second i had some issue with my script calling the correct file, yet that is my own fault with my laziness on my script, and not having the time to correct it...

Thank you for brainstorming with me...

Cheers!!!
E

---

### Post by matey3 on 2009-07-31
e24ohm;
Yes happened to me as well, the seconds %S helped out
Regards;

---

### Post by e24ohm on 2009-07-31
> **matey3 said:**
> e24ohm;
Yes happened to me as well, the seconds %S helped out
Regards;It helped out a great deal. Once i get back to the client, early next week, i am going to use the example you gave for your "rsync" settings, and switches.

thanks again.
E

---

