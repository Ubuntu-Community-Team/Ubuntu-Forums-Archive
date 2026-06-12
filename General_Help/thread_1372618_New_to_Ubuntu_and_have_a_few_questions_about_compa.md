---
title: "New to Ubuntu and have a few questions about comparing folders"
date: 2010-01-04
forum: General Help
---

### Post by vdubhack on 2010-01-04
I am in the need to compare the contents of two - four folders. The way I need to compare them is as follows:
Date created/modified
size
compare all contents in folders including subdirectories
If something exsists in one and not the other.
any modifications of files will be confirmed before changing and what the difference is
Basically these need to be mirrored copies and if one gets an updated file the rest when compared need to update accordingly or if something is deleted from one it will be added back in the next comparison.

I have found the diff and rsync commands but I am lost as to as to get the correct triggers for what I want to do. I am also new to scripting and I am pretty sure this could be done with a script but not sure how to write one to work how I need. Anyone have any good tricks they can share or point me in a direction to read something that can show me how to accomplish what I need to do. 

Thanks!

---

### Post by Jive Turkey on 2010-01-04
So are these pairs of four folders?  That should be pretty easy.  If you have a set of more that two you will need to plan it out as I think diff and rsync only deal with pairs.

Im not familiar with diff but I know rsync has a dry-run option that just outputs what it would have done and it lets you reference include/exclude lists.

You could also use grsync which is a gui frontend to rsync, which exposes the command it is running.  There are more options than those presented by the grsync interface.

In a terminal you can use "man <nameofprogram ie rsync>" to view the manual page and press 'q' to quit the manual page and return to the cli.  with some study you should be able to create a bash script that will do you syncing just how you like and then create a cron schedule to make it happen as often as you like.

---

### Post by jamesisin on 2010-01-04
Someone has been helping me with creating a script and cron job for rsync from which you might be able to benefit:

[http://ubuntuforums.org/showthread.php?t=1366759&page=2](http://ubuntuforums.org/showthread.php?t=1366759&page=2)

---

### Post by mbeach on 2010-01-04
would a version control system like git do the job for you? You may want to create another folder to house the 'official' folder which is the result of the merges of the other four, then each of the other four checkout the official folder. Also provides you with a history.

links:
git:  [http://git-scm.com/](http://git-scm.com/)

or something else which looks interesting:
[http://linux.softpedia.com/get/System/Backup/Persy-51573.shtml](http://linux.softpedia.com/get/System/Backup/Persy-51573.shtml)

---

### Post by vdubhack on 2010-01-04
Thanks for the replies so far I am reading the thread you listed to see if I can grasp it and make it work for how I need it to. 

I cant do it with one main file as the fall back as some files will be added to say one folder only but will need to be added to the other folders when I check them. And its not always the same folder where the difference occurs it can be any one of 4 folders that gets something added new to it.

Not sure if I got the question if they were pairs of 4 folders. Its four seperate folders. 3 on 3 different computers. One on a removable HD that houses all the true backups of all the differences from the 3 computers. Hope this helps make more sense

---

### Post by jamesisin on 2010-01-04
If you are talking about 3 users on 3 machines making changes to 1 set of data in a folder, you would look for a way to keep those files on one machine and share them with the other 2.  Reason: you will run into version problems and over-writes when 2 users change 1 file between syncs.

If you are talking about 3 users on 3 computers making changes to 3 sets of data in 3 unique folders, you will merely need to create 3 scripts (1 for each machine) to accommodate your backups.

---

