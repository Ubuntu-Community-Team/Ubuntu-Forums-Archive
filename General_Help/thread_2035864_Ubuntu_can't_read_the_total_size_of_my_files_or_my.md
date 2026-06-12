---
title: "Ubuntu can't read the total size of my files or my HD"
date: 2012-07-31
forum: General Help
---

### Post by jontin on 2012-07-31
Hi all, 

I'm trying to backup my system right now, but it keeps telling me that the external HD (500GB) is too small to back up the 4.7 PB that I have on my laptop. 

Needless to say, I don't have anything close to 4.7PB on my laptop. I am using about 30 GB of a 120GB partition of my harddrive

 I tried to copy the "home" folder manually to the external HD without using Deja Dup, and it is doing the same thing.

Do we know what could be causing this?

Suggestions? Ideas? 

Thank you!
Jon-tin

---

### Post by drmrgd on 2012-07-31
Could it be that you have something mounted in /home?  I sometimes forget to disconnect some network shares that I mount in /home when I try to do a backup, but quickly realize that the TBs of data that it wants to backup can't possibly be in my directory.  

You can double check the culprit with a quick disk usage query along the lines of :

```
du -kh /home | sort -n | tail -n 10
```

That'll show you the top 10 folders in your /home directory according to size.

---

### Post by jontin on 2012-07-31
Hi there, 

I ran the above command, and the biggest file to come up on the list was 1008 megabytes. I don't have any servers or larger databases connected to my computer, so it wouldn't be counting that instead...

EDIT: On second read of your post, there's something going on here that I need to take a second look at. I'll post again when I have looked closer at what that command was telling me.

---

### Post by jontin on 2012-07-31
Update: 

The above command gave me a list of areas to have a look at, but none of them listed the location of a .odt word file that was listed as taking up 4.7 PB of space. 

I decided to check the folder sizes of various locations, and managed to narrow it down to a file that was listed as 4.7 PB. The fact that it was not listed when I entered the command above seems to re-inforce the obvious, which is that I didn't have such a large file on my HD, but in fact the file was just saying it was that big and preventing me from doing a system backup. 

I tried to open the file, as an aside, and it seemed like there was a problem with the script. I have deleted it and emptied the trash, and I have been able to backup my system. 

Now onto other issues!

Thanks for your help
Jontin

---

### Post by erind on 2012-07-31
> **jontin said:**
> Update: 

The above command gave me a list of areas to have a look at, but none of them listed the location of a .odt word file that was listed as taking up 4.7 PB of space. 

I decided to check the folder sizes of various locations, and managed to narrow it down to a file that was listed as 4.7 PB. The fact that it was not listed when I entered the command above seems to re-inforce the obvious, which is that I didn't have such a large file on my HD, but in fact the file was just saying it was that big and preventing me from doing a system backup. 

[...]

There's a similar issue described in this thread too:

    [http://ubuntuforums.org/showthread.php?t=2029494](http://ubuntuforums.org/showthread.php?t=2029494)

Perhaps it would help.

---

### Post by Skaperen on 2012-07-31
I hope you did not back up the filesystem to your only backup copy.  You should at least rotate your backups to 2 or more drives, and check to be sure a restore can be done or that the data is valid.

The reason I'm concerned is that if a file is listed as 4.7PB then something is corrupted in the filesystem.  A backup should have been done with an exclusion for that file, then a filesystem check run to let it see if it can correct the file.  You should still run a filesystem check after having deleted the file.

Whatever caused the corruption might have also caused this file to "point to" data blocks belonging to other files.  The delete would have marked those blocks as "unused and now available".  Writing new files could destroy the data of other existing files.  Filesystem checks can correct this if it is not too late.

---

### Post by jontin on 2012-08-01
Thanks everyone for your help so far. 

So, the foray into Ubuntu nerdiness begins. I have been avoiding it for a long time, but I have no choice now because of a few other things I am trying to do!

I looked up the "fsck" command and generally understand what is required in order to it. Most of the tutorials out there seemed to assume that I knew more than I do, but this one seemed to be easy enough to follow: 

[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

One thing I am wondering is if the "disk utility" application's option that says "check filesystem" will do the same thing as the "fsck", command, or if I should do both? 

I do understand that this may be pointing to a larger issue. The windows side of my partition is blue-screening without even being able to get to the login for Windows, so there is some cause for concern in that regard. 

PS, don't worry about me  writing over my previous backup. I didn't even have one ;-)  This is the start of some long-neglected computer maintenance for me.

---

### Post by drmrgd on 2012-08-01
Yes, it does look like you might be starting to see the tip of some potential drive problems.  I believe that the "check filesystem" utility in the Disk Utility program is not the same as fdisk, but is very similar such that running both isn't necessary.  

Not that age necessarily matters, but how old is the drive?

---

### Post by jontin on 2012-08-01
Hi, 

The drive is four years old.  

I tried to unmount the partition with my ubuntu on it in the both the "disk utility" and the terminal and it said in both that the overall drive is busy (simply named "/") 

Every once and a while, ubuntu does a check of my system before I start up. Would this be effectively doing the same thing that I'm looking for? Similarly, I went into recovery mode and ran a check disk by mounting my drive as read-only. I couldn't really understand what it was telling me when I did that. 

If neither of these are going to give me a full analysis of what's going on with my drive, I'll continue to try to figure out how to fsck. 

-Jonathan

---

### Post by zero2xiii on 2012-08-01
Hay,

/ is the rot partition.

You need to run fsck offline, in other words the drive you want to check has to be unmounted and unused. / is like C:/ on windows. It is where linux is installed, you cannot unmount the drive your computer is running from :).

What you need to do is boot from a live CD and then run the fsck command from the live system on the drive you want to check. This is by far the easiest option.

Cherz

---

