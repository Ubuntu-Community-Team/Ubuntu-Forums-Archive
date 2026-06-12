---
title: "What is preventing my HDDs from sleeping?"
date: 2006-06-09
forum: General Help
---

### Post by Strid on 2006-06-09
Hello,

I've been using Ubuntu now for more than 1½ year, and I must say, that I love it.
I recently upgraded my computer and my new computer is, in fact, really quiet. I have fanless PSU and the only fan in my computer is a Zalman that is almost inaudible.

Now, what bothers me is that my harddisks won't turn them selves off. I've been searching various forums and google'ed alot, and this is the solution I've found (though it doesn't really work - explanation to come):

```
anders@t50-ubuntu: ~$ sudo hdparm -S 18 /dev/hda
anders@t50-ubuntu: ~$ sudo hdparm -S 18 /dev/hdb
```

This would make my HDD's spin down after 1½ minutes of not being accessed. Now the thing is, that they often never get to spin down, and if they do, they won't stay for long.
My hda is where ubuntu and all programs are located, and hdb is where I keep my data (MP3, movies, etc). I could understand it, if hda didn't turn off, but hdb won't turn off, and that is something that bothers me, because no program should access that drive, unless I wanted to listen to MP3 or somthing.

Now, obviously the cause is that some process is accessing the disks. So my questions are:

1) How do do I identify the harddisk-accessing-program, so I can (if possible) disable it? 

2) Is there a better way to control harddisk sleep mode than "hdparm -S"?

3) Thats all. :wink: 


Best regards,
Anders Christensen

---

### Post by mannheim on 2006-06-09
Does hdb go to sleep after the requested time if you log out and just wait? Or does it stay awake even then?

(Every time I launch firefox on my ubuntu machine, it wakes up the sleeping usb drive that is attached to another computer on my home network! I've no idea why. But that suggests that if I just use firefox, then my local hard disks aren't going to be given a chance to go to sleep.)

---

### Post by Strid on 2006-06-09
Didn't seem to work if I logged out - or I didn't wait long enough. I tried to do a "ps aux" (a friend told me that) to see all the processes that I have running i the background. All I got from it was a rediculos long list what what i wanted, and I don't really know the names of all I've got running and what it does. :)
This is one of the few areas, where Windows (eeeek!) did better than Ubuntu does. :-S

---

### Post by huygens on 2006-06-23
This problem (which I still have) has been discussed in 2 threads that I know during the dapper testing. Some solutions (that did not work for me, but did for others) have been proposed. You might be interested in reading them:
[http://www.ubuntuforums.org/showthread.php?t=153951](http://www.ubuntuforums.org/showthread.php?t=153951)
[http://www.ubuntuforums.org/showthread.php?t=150168](http://www.ubuntuforums.org/showthread.php?t=150168)

Huygens

PS: my hardrive is about 6°C higher on Ubuntu than on Windows (and it feels really hot as it is under the palm of your hand when I am writing on my laptop), it has regular activity avoiding it to go to sleep, and most of all I suspect it to be my battery power drainer, I have a couple of hours of autonomy instead of 4hours under Windows.

---

### Post by huygens on 2006-06-29
So, do you still have the problem? Or is it solved for you?
I would be really interested in your answer as I still have the problem.

After analysis, if I let run my PC with barely nothing opened (no network, no services, etc.) I have network activity every now and then. To measure it, I have used iostat. Every 5 minutes about 800 blocks are written.
To find the culprit, I have tried the -mmin options of the find command. The result is: no file has been modified!!!

My conclusion is that the journaling system (or something of the sort) is causing this constant writing. As I am using XFS for my / partition and JFS for my /home partition, I do not know which one is causing the problem :confused: 

Does any one use a XFS or JFS partition and could try to diagnostic whether he/she has also constant disk access?

Huygens

---

### Post by LazyBoy on 2006-07-03
Yes.  All journalling file systems write the disk every few seconds.  Google on "spin-down" and "journalling" and you'll find lots of discussions.

You could use ext2, but not using a journalling fs has certain drawbacks.  Also non-laptop disks aren't designed for a lot of spinups and spindowns.  You'll want to estimate your accesses/time and do some math to see if the resulting lifespan is acceptable.

LB

---

### Post by huygens on 2006-07-05
I will then check Google. There should be a way to state that when on battery, the journal writing on the disk should be delayed longer than when not on battery.
Also, I am surprised that when there isn't obvious activity from processes regarding disk read or write, the "journaling" system is still active... I thought that journalling was just that prior to write the data to the disk, the journal of the operation is written with high priority, so in case of crash during the "dump" of the data, the filesystem can recover by reading the journal and rollback the last failed operation. So the check on boot time is much faster, and the disk integrity safer.
So in my case, I do not really why the journalling would be activated :(

Huygens

---

### Post by Aviatrixie on 2006-07-05
What is preventing my HDDs from sleeping?

Maybe your CD/DVD-ROM snores?

sawwy... I had to respond!:lol:

---

