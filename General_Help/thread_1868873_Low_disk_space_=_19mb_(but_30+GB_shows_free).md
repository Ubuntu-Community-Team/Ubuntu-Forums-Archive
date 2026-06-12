---
title: "Low disk space = 19mb (but 30+GB shows free)"
date: 2011-10-24
forum: General Help
---

### Post by pjstock on 2011-10-24
I am getting a warning that I am down to 19Mb of free space.
But I have cleaned up, backup, backed off, deleted as much stuff as I can find.
and when I look at Properties of the various areas of the File System I am showing some 31Gb free (on a 250Gb Drive.)

There are two users accounts on this machine and I expect I have somehow messed up the rights and permissions.

I've attached here various screen shots that should show what I am seeing (but not understanding.)
what am I doing wrong? where is the bottleneck here on HDD space?

Many thanks 

Peter

---

### Post by duke.tim on 2011-10-25
Using bleachbit can cause this warning, if that is the case don't worry abour it. Try restarting (or logging out and in) it might be persistant after clean up untill then. 

This thread talks about low disk space:
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by pjstock on 2011-10-25
thank you. lots of interesting and I am sure helpful information here.

but I must say this Ubuntu linux stuff remains incredibly arcane. someone will make a fortune making this simple to use and manage.

Let me start by putting this out there:

julie@julie-desktop:/$ df -Th | sort
/dev/sda1     ext3     19G   18G   52M 100% /
Filesystem    Type    Size  Used Avail Use% Mounted on
none      devtmpfs    750M  284K  750M   1% /dev
none         tmpfs    754M  332K  754M   1% /var/run
none         tmpfs    754M  532K  754M   1% /dev/shm

what the Hey does this all mean?
if I am reading correctly this partition (is that right?) is sized at 19G but somehow 18G of it is used, leaving just 52Mb or 1%?

is that the correct read?

if so then I have to figure out how I managed to allow this to burn up 18G of the 19G on the main partition.

(why is this so complicated?)

---

### Post by dcstar on 2011-10-26
> **pjstock said:**
> thank you. lots of interesting and I am sure helpful information here.

but I must say this Ubuntu linux stuff remains incredibly arcane. someone will make a fortune making this simple to use and manage.

Let me start by putting this out there:

julie@julie-desktop:/$ df -Th | sort
/dev/sda1     ext3     19G   18G   52M 100% /
Filesystem    Type    Size  Used Avail Use% Mounted on
none      devtmpfs    750M  284K  750M   1% /dev
none         tmpfs    754M  332K  754M   1% /var/run
none         tmpfs    754M  532K  754M   1% /dev/shm

what the Hey does this all mean?
if I am reading correctly this partition (is that right?) is sized at 19G but somehow 18G of it is used, leaving just 52Mb or 1%?

is that the correct read?

if so then I have to figure out how I managed to allow this to burn up 18G of the 19G on the main partition.

(why is this so complicated?)

You have (at least) two partitions. One is the root partition and it is full. The other is not the root partition and it is not full. The root partition is critical for the system to operate correctly.

Do a forum search for the many posts that already exist for solutions to full root partitions.

---

### Post by varunendra on 2011-10-26
The 'disk usage analyzer', combined with default linux permission policies, is a very interesting and useful thing. By default it shows the usage of only those directories to which you, as a normal user, have access to. To see the usage statistics from 'everywhere' you will have to run it with root-access permissions. To do so, open it as follows:

Press Alt+F2 to bring up the "Run Application" dialogue box, then type
```
gksu baobab
```and press 'Enter'. This will open it with root access permissions. Click on the 'hard-drive' icon at its top to scan entire filesystem. Now you can see which directory (including system ones) has occupied how much space.

In case of multiple partitions mounted on the filesystem, you also need to know which partition is mounted where in the filesystem, so that you can figure out how much space is physically occupied on a particular partition. To see this mounting info the command is simply:
```
mount
``` In the result of the above command, look for the entries like /dev/sda1, /dev/sda2 etc. These are your partitions.

Once you know which partition is having space problem, you can proceed to move/delete unnecessary stuff on it to free space.

As dcstar pointed out, me too doubt it's your root partition having the problem. It can be cleaned by moving/removing older kernels (if any) or downloaded packages. Using the disk usage analyzer as root will also tell you if there are any user-files created in the root's home folder or in his trash (which can't be accessed in normal user mode).

---

### Post by Slim Odds on 2011-10-26
By default, the formatters used by Ubuntu (and most linuxes it seems) reserves 5% of the of the file system for root access. This space was once needed to allow repairing a full system in-place. Since we can now use bootable CD's or USB's, this is a waste of space (especially for /home, since it was never needed there).

You can reclaim this space by using tune2fs with either the -m or -r options. [http://linux.die.net/man/8/tune2fs](http://linux.die.net/man/8/tune2fs)

---

### Post by varunendra on 2011-10-26
> **Slim Odds said:**
> Since we can now use bootable CD's or USB's, this is a waste of space (especially for /home, since it was never needed there).

You can reclaim this space by using tune2fs with either the -m or -r options. [http://linux.die.net/man/8/tune2fs](http://linux.die.net/man/8/tune2fs)
Reclaiming 'all' the reserved space is, IMHO, not a good idea, and may cause system failure. IIRC, it was set to 5% in older days of low capacity hard drives assuming it will total to 200MB or more which is essential for background maintenance tasks. So I think at least 1% should still be kept reserved for the same purpose (or less, if possible in tune2fs, to keep it between 200MB to 1GB).

But in the case of OP, I still doubt there is some obsolete data occupying space on root partition (apart from this default reserved space of course - which may already be too small if the root partition itself is a small one).

---

### Post by Slim Odds on 2011-10-26
> **varunendra said:**
> Reclaiming 'all' the reserved space is, IMHO, not a good idea, and may cause system failure. IIRC, it was set to 5% in older days of low capacity hard drives assuming it will total to 200MB or more which is essential background maintenance tasks. So I think at least 1% should still be kept reserved for the same purpose (or less, if possible in tune2fs, to keep it between 200MB to 1GB).

But in the case of OP, I still doubt there is some obsolete data occupying space on root partition (apart from this default reserved space of course - which may already be too small if the root partition itself is a small one).

I've set my reserved space to 0% on all my systems for the past 5 years, no issues. The only possible place it could even be useful is for the / partition.

You should note that the "reserved" space is reserved for root, which Ubuntu does not even use.

If you feel that this space is needed, please explain exactly why.

It is absolutely not needed for /home and with large drives it wastes a TON of space.

---

### Post by varunendra on 2011-10-26
> **Slim Odds said:**
> You should note that the "reserved" space is reserved for root, which Ubuntu does not even use. Ever tried "gksu nautilus"? I use it too often. It opens nautilus in root directory and root's trash becomes your trash. I think the same thing happens when you run any command with sudo (which you already know is how frequent). So although you didn't log-into root, you used its directories and configuration files.

> **Slim Odds said:**
> If you feel that this space is needed, please explain exactly why.

It is absolutely not needed for /home and with large drives it wastes a TON of space.I think it is quite well explained here: [https://wiki.archlinux.org/index.php/Ext3#Reclaim_Reserved_Filesystem_Space](https://wiki.archlinux.org/index.php/Ext3#Reclaim_Reserved_Filesystem_Space)

It may not need to be 5% on larger drives, but IS definitely needed if you are going to fill up the whole drive and still desire for a decent performance.

---

### Post by Slim Odds on 2011-10-26
> **varunendra said:**
> Ever tried "gksu nautilus"? I use it too often. It opens nautilus in root directory and root's trash becomes your trash. I think the same thing happens when you run any command with sudo (which you already know is how frequent). So although you didn't log-into root, you used its directories and configuration files.

I think it is quite well explained here: [https://wiki.archlinux.org/index.php/Ext3#Reclaim_Reserved_Filesystem_Space](https://wiki.archlinux.org/index.php/Ext3#Reclaim_Reserved_Filesystem_Space)

It may not need to be 5% on larger drives, but IS definitely needed if you are going to fill up the whole drive and still desire for a decent performance.

Firstly, if you're filling up your drive that much, it's time to buy new drives. Once again, that concept of reserved space is from a bygone era when drives were much smaller and more expensive.

Secondly, from that that page you quote:> Ext3 partition contain a used space of 5% for special reasons by  default.  The main reason for such space is so root can log in even when  the filesystem becomes 100% used.  Without this option, the root user  might not be able to log in to "clean up" because the system could  become unstable, trying to write logs to a 100% full system for example.   The other reason is to help with less fragmentation on the filesystem. 

So it's not talking about "gksu", but actually logging in as root.

Sure, if you setting up a server, but all means leave some reserved space. But for a desktop user it a complete waste.

whatever....

---

### Post by duke.tim on 2011-10-26
Non-server, Ubuntu Desktop systems write logs as root...

Reducing the size seems prudent, but eliminating it seems dangerous,
depending on how gksu/sudo function (which I am inspired to look into suddenly LOL)

---

### Post by varunendra on 2011-10-26
> **Slim Odds said:**
> Firstly, if you're filling up your drive that much, it's time to buy new drives. Once again, that concept of reserved space is from a bygone era when drives were much smaller and more expensive. In my HP Compaq dx2480 I have right now 3 hard drives, 2x360GB and 1x500GB. Apart form my normal office data files (which include both finished and raw video files for our multimedia related work), I have lots of ISOs, VM's, and of course those heavy windows applications (in the windows part), games and 100s of movies. Of the five data partitions (ranging from 60 to 258 GB), only one has 50+ GB space, one has 10+ GB space, and none other have more than 4-6GB space. I don't think my scenario is unique. :)

> **Slim Odds said:**
> Secondly, from that that page you quote:

So it's not talking about "gksu", but actually logging in as root. What I mean is, if you ran a GUI application with gksu or sudo, it may (and most often will) start creating/saving its user-data in the root's home (for example creating an iso with gksu brasero). Of course "we" can control in most of the cases what the user-directory should be even in that case, but you won't disagree we are providing instructions for non-geeks here - simple innocent users who may not be yet familiar with linux policies and methods. If you want an example (I've faced some and remember at least one), search posts by "ginzell" (won't be many). That was the first time when I had to dig out the use of "gksu baobab" to solve the root's trash confusion creating similar "where-did-my-space-go" problem.[/quote]

> **Slim Odds said:**
> Sure, if you setting up a server, but all means leave some reserved space. But for a desktop user it a complete waste.again, only if we assume you got all that space only to never use it up :). Else, fragmentation = performance loss.

---

### Post by duke.tim on 2011-10-26
This seems to be the general consensus of what I've found on the web
[http://askubuntu.com/questions/19504/reasonable-size-for-filesystem-reserved-blocks-for-non-os-disks](http://askubuntu.com/questions/19504/reasonable-size-for-filesystem-reserved-blocks-for-non-os-disks)
> If you set the reserved block count to zero, it won't affect performance much except if you run for long periods of time (with lots of file creates and deletes) while the filesystem is almost full (i.e., say above 95%)

In short If the filesystem is almost full, reserve 5% for filesystem management (not even taking into account things for root services). I wouldn't include gksu or sudo as root services, but an additional avenue for filling up the reserved space. Reserved filesystem space only really becomes important if the drive is filled.

It is more of a case where the user has a filled filesystem, such as the case with the OP. It is a good Idea to buy a larger capacity drive, but we can not assume that all users will be able to afford that solution (at least in the short term). Considering how much storage space has been consumed, It would be reasonable not to eliminate the reserved filesystem space. [s]Especially since It appears that the OP has only 1 partition (used as storage space e.g. /dev/sda1).[/s] *It appears in the pictures that there is indeed a storage partition 0.o

If reduction of the reserved space was to be done
Since it is reporting a size of 19G, 18G used [18-19=1G=1024M], and 52M Availible 1024-52=972M
Meaning 972M within reserved 
Right? 
If the minimum safe reserved is 200Mto500M
It can be **SAFELY*** reduced between 772 and 472

***Safely not including the 5% the file system seems to need in some cases.**

^ that would be using the quoted df command

---

### Post by varunendra on 2011-10-26
> **duke.tim said:**
> 
Since it is reporting a size of 19G, 18G used [18-19=1G=1024M], and 52M Availible 1024-52=[COLOR=Red]**972M**[/COLOR]
Meaning 972M within reserved 
Right? 
If the minimum safe reserved is 200Mto500M
It can be **SAFELY*** reduced between 772 and 472Perfect calculation!! :D

5% of 19GB = 972.8 MB
and,
200MB = 1% of 19 GB

Gain+available = 772.8+52 = **824.8MB**

We got here the use of tune2fs :)

---

### Post by duke.tim on 2011-10-26
Whew! :lolflag:

---

### Post by jwbrase on 2011-10-26
> **dcstar said:**
> You have (at least) two partitions. One is the root partition and it is full. The other is not the root partition and it is not full.

Wrong. Look at his screenshots: The properties dialog for his ~/Desktop folder is showing 19 MB free, the 32 gig free figure is for /media/e02755...

If anything, his root partition is fine and his home partition is full.

But the df output he posted only seems to mention 1 disk partition.

@pjstock: Log in as the user you were logged in as when you took your screenshots. If you had external drives plugged in when you took the screenshots, plug them in. If you had drives mounted that aren't normally mounted, mount them.

Run gparted (gksudo gparted). There should be a drop down menu in the upper right corner, which should be labeled with something like "/dev/sda (XYZ GiB)." Don't touch anything else, but select each drive in that menu (there may only be one drive, however, depending on the configuration of your computer) and take a screenshot with that drive selected. Then exit gparted. Post the screenshots here.

Also, is this a Wubi install or otherwise dual booted with Windows?

---

### Post by varunendra on 2011-10-26
> **jwbrase said:**
> Wrong. Look at his screenshots: The properties dialog for his ~/Desktop folder is showing 19 MB free, the 32 gig free figure is for /media/e02755...

If anything, his root partition is fine and his home partition is full.

But the df output he posted only seems to mention 1 disk partition.
You are correct! And now it got a bit confusing to me too. The screenshots were posted from user "peter", while df was posted from user "julie". It is best we get screenshots of gparted. Although the tune2fs trick will still work nonetheless, the screenshots will just determine 'where' it is needed (maybe everywhere..).

---

### Post by duke.tim on 2011-10-26
I'm betting that the df command was quoted from another thread.

---

### Post by jwbrase on 2011-10-26
> **duke.tim said:**
> I'm betting that the df command was quoted from another thread.

Well, he probably got the idea to use it from another thread (I don't know why he'd have posted the results of "df -Th | sort" instead of just "df -Th", other than finding that recommended in a thread and not knowing that the "sort" part isn't necessary). 

I don't think he posted the results from another thread, though: He's said there are two accounts on the machine, one account shows up in the screenshots, another where he pasted the results of df, and the account names "peter" and "julie" match up with the initials on his forum account. That matches up perfectly with him having actually run "df -Th | sort" on his own machine.

---

### Post by pjstock on 2011-10-27
> **dcstar said:**
> You have (at least) two partitions. One is the root partition and it is full. The other is not the root partition and it is not full. The root partition is critical for the system to operate correctly.

Do a forum search for the many posts that already exist for solutions to full root partitions.

Thanks David.
but I have done a search on the forums for "full root partition" and have then scroll through about 10 pages of threads and none seem to propose solutions for my situations. (or at least none that a mere mortal like me could understand.)

I will keep plugging.

Peter

> **varunendra said:**
> You are correct! And now it got a bit confusing to me too. The screenshots were posted from user "peter", while df was posted from user "julie". It is best we get screenshots of gparted. Although the tune2fs trick will still work nonetheless, the screenshots will just determine 'where' it is needed (maybe everywhere..).

ahh here we are. and here I am again.

Backstory. 
I originally set this machine up for my partner Julie and so set her as administrator.
I set myself up as a secondary user (Peter)  to have access to the 2ndary HDD which had a whack of music and so that I could use it across our home LAN for file backup.

and then Julie got fed up with Ubuntu and bought a Mac.

so I recovered this machine as my main home machine (everyone following here?)
but because I can't figure out (i.e. "am too stupid to figure out") how to get rid of the Julie user and simplify it to just one user (me, Peter) I have been floundering around and then came face to face with this out of space error. 
which seems bizarre because this is basically a web surfing machine. we don't actually USE it for anything.

Peter (on behalf of Julie.)

> **jwbrase said:**
> Wrong. Look at his screenshots: The properties dialog for his ~/Desktop folder is showing 19 MB free, the 32 gig free figure is for /media/e02755...

If anything, his root partition is fine and his home partition is full.

But the df output he posted only seems to mention 1 disk partition.

@pjstock: Log in as the user you were logged in as when you took your screenshots. If you had external drives plugged in when you took the screenshots, plug them in. If you had drives mounted that aren't normally mounted, mount them.

Run gparted (gksudo gparted). There should be a drop down menu in the upper right corner, which should be labeled with something like "/dev/sda (XYZ GiB)." Don't touch anything else, but select each drive in that menu (there may only be one drive, however, depending on the configuration of your computer) and take a screenshot with that drive selected. Then exit gparted. Post the screenshots here.

Also, is this a Wubi install or otherwise dual booted with Windows?

This is just a plain vanilla Ubuntu install. from scratch. there is no Windows anywhere on this machine. (indeed Ubuntu was intended to be an Windows replacement.)

I expect that the screenshots I posted (it has been a week or so and when you are just blundering around in the dark, you don't always remember how you got where you are.) were when I logged in as Julie (as that user is the administrator and so I figure should have had a more complete view of the system.)

but I think I read somewhere that I should Unmount extraneous drives and I think I did that before I took the screen shots (too much information, not enough knowledge - mine.) 

I will reboot or remount the 2nd HDD, re do the screen shots (from Julie? the original main user? I have no clue on the terminology. Root user? Administrator? main user...?)

> **varunendra said:**
> You are correct! And now it got a bit confusing to me too. The screenshots were posted from user "peter", while df was posted from user "julie". It is best we get screenshots of gparted. Although the tune2fs trick will still work nonetheless, the screenshots will just determine 'where' it is needed (maybe everywhere..).

voila.
thanks for all your patience and help

---

### Post by varunendra on 2011-10-28
Good job!

So now in the hindsight it all seems not-so-complex or confusing and maybe we were just being a bit ignorant :).

The summary is: you have a 20GB hard drive on which you have only root (/) and swap partitions (with /home 'inside' the root partition), and another 250GB hard drive which holds all your music and stuff. Although gparted shows 993.57 MB of free space on your 18.4GB root partition, it does not tell anything about how much of that space is still reserved (leaving you, as a normal user, with the remaining space). So:

[LIST]
[*]did you use *tune2fs*?
[*]If so, how much space did you keep as *reserved*?
[*]did you figure out which of the contents have consumed most of the space and whether some of them are obsolete? (use of *gksu baobab*)
[/LIST]
Even if you change the reserved space to 0% (which I won't recommend), it won't take long to fill up that 993 MB remaining space. Hence I have a quick suggestion for you:

With such a small size of root partition (combined with Ubuntu 10.04 is it?), you should consider either creating your /home partition on the larger drive, or better, manually move all the user data to it, and keep doing it from now on. It is my preferred method to maintain space on my root partition (keep /home within root, but keep all user-data somewhere else). Even though I have a lot of space to spare, I keep my root partition between 20-26GB (with /home), and never had a problem with this kind of data management policy.

I'd be happy to help figuring out what or what not you can move or delete from your root partition.

---

### Post by pjstock on 2011-10-28
> **varunendra said:**
> Good job!

The summary is: you have a 20GB hard drive on which you have only root (/) and swap partitions (with /home 'inside' the root partition), and another 250GB hard drive which holds all your music and stuff. 

Thanks but I think or I thought that I had a 250Gb primary drive and a 500Gb alternate HDD (and THAT one was to be used for Music and backup files etc.). 

Or at least that is what I bought and installed.

However, when I was trying to get a handle on this size problem, to eliminate possibly confusing elements, I did completely disconnect the 500Gb HDD. I was getting confused about what was where. So, at this time there is only a single 250Gb HDD in there.

[ opps correction. I reconnected the 500Gb drive via external USB connection, rebooted and it is showing. See screenshot below.  SO yes, I have a 250Gb internatl HDD and a -- now connected externally but originally internal as a 2ndary drive -- 500Gb. ]

I also THOUGHT that I had initially partitioned it with a chunk for the boot partition and the balance for data.

But I am not at that machine now and I am certainly confusing things.

---

