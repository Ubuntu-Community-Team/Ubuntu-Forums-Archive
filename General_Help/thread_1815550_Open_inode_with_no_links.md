---
title: "Open inode with no links"
date: 2011-07-31
forum: General Help
---

### Post by rpaskudniak on 2011-07-31
Greetings, Family.

I thought it might be a refreshing change in this forum to ask a scholarly question about a nuts-and-bolts issue of a functioning system.  My question applies to any flavor of Linux or Unix.

Some time ago someone in my group spawned a runaway instance (among many) of a daemon that was generating mucho megabytes of log each minute.  I could run *df* and watch the available space on the file system dwindling.  For some reason (mainly, I couldn't tell which instance was the rogue), I was unable to kill it.  In a panic, I deleted the log file.  Ah, all I did thereby was shoot myself in the foot. Since the file was still open to the daemon logger, the logger was continuing to eat the file system; all I had succeeded in doing was removing its link; the inode was still there and the file still growing.  And I could not even find the inode now, since the *ls -i* command needs a link name to show me the inode number.

I contacted the Unix SA group, who were able to track down the inode and the PID of the rogue.

(Whew) My bottom line question:  What did they do?

What command (or sequence of commands) can the SA use to list inodes in a file system, give me their link names, and - most important - note the lack of a link name?  (Some special option to chkdsk?)

And then, what option (or alternative) to fuser exists to see which PID has that inode open?  Or can fuser be used for this whole exercise? :-k  I'm looking at an [_about.com page on fuser_]("http://linux.about.com/library/cmd/blcmdl1_fuser.htm") but it's missing that detail.

I'm all ears! (I was looking for a smiley that represents a donkey. ;) )

Thanks much for ideas.  This has been kicking around in my head for some time.

---

### Post by tredegar on 2011-07-31
> I contacted the Unix SA group, who were able to track down the inode and the PID of the rogue.

(Whew) My bottom line question: What did they do?
Errr, why don't you just ask _them_ ?

---

### Post by rpaskudniak on 2011-07-31
Tredegar asked:
> Errr, why don't you just ask them ?
Two reasons:
1. They wouldn't tell me the first time I asked.
2. I'm long out of there.

I was reminded of this because I was asked a tangentially related question on a phone interview.  I consider myself lucky the interviewer did not ask me how I would handle it. [-o<  But he might ask it in the next interview.

---

### Post by tredegar on 2011-07-31
OK.

But how can they "not tell you"? 

Did you *gave them access* to your system to kill this rogue process? If we are going to be discussing scholarly questions, this would seem most unwise, but perhaps I have misunderstood the situation.

---

### Post by rpaskudniak on 2011-08-07
Sighh.. I am surprised this thread has bogged down this way.  It happens that the SA's have access whether or not I give it to them.  They normally intervene when asked for help.

But what's stopping other advice from coming in?

Let's boil the problem down to a couple of essential How-to questions:
[LIST=1]
[*]What Unix/Linux command (issued from the shell) will yield a list of open inodes in the current running system, whether or not there is a file name (AKA link) associated with that inode?  Some option to fuser I have missed, perhaps?  Or maybe something in the /proc file system (which is not universal, AFAIK)?
[*]If I have an inode number but no link name, is there a way to create a directory entry (i.e. a link name) that references that inode?  That way I can use fuser to see the PID of the process that has it open and kill that process.  Also makes it easier to rm it (after killing that PID), as noted in the follwing item:
[*]Is there an option (or alternative) to the rm command that will remove a file given only the inode number?  I have found a [[COLOR="Blue"]_"find" command_[/COLOR]]("http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html") that will remove the file by name if it's inum matches something:```
$ find . -inum 782263 -exec rm -i {} \;
```but this still assumes there is a link name with which to execute the rm command.
[/LIST]
Interdeparmental politics aside, does anyone know of [as willing to share] methods to accomplish this kind of SA wizardry?

Thanks much!

---

### Post by haqking on 2011-08-07
> **rpaskudniak said:**
> Sighh.. I am surprised this thread has bogged down this way.  It happens that the SA's have access whether or not I give it to them.  They normally intervene when asked for help.

But what's stopping other advice from coming in?

Let's boil the problem down to a couple of essential How-to questions:
[LIST=1]
[*]What Unix/Linux command (issued from the shell) will yield a list of open inodes in the current running system, whether or not there is a file name (AKA link) associated with that inode?  Some option to fuser I have missed, perhaps?  Or maybe something in the /proc file system (which is not universal, AFAIK)?
[*]If I have an inode number but no link name, is there a way to create a directory entry (i.e. a link name) that references that inode?  That way I can use fuser to see the PID of the process that has it open and kill that process.  Also makes it easier to rm it (after killing that PID), as noted in the follwing item:
[*]Is there an option (or alternative) to the rm command that will remove a file given only the inode number?  I have found a [[COLOR=Blue]_"find" command_[/COLOR]]("http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html") that will remove the file by name if it's inum matches something:```
$ find . -inum 782263 -exec rm -i {} \;
```but this still assumes there is a link name with which to execute the rm command.
[/LIST]
Interdeparmental politics aside, does anyone know of [as willing to share] methods to accomplish this kind of SA wizardry?

Thanks much!

i am pretty sure debugfs has a switch for showing inodes ?

and i may be misreadig what you mean but wont the ln command assist in number 2 ?

as for number 3 i was gogin to say the find command

---

### Post by rpaskudniak on 2011-08-07
Ah!  Someone has taken a crack at at it.  Thank you, haqking!

Point 1: As you can see, I had already obviated the possibility of using _**find**_ for this purpose since my problem involves the lack of a file name for the inum and *find* depends on having an inum, even if I had done the search by inum.

debugfs? That's a new one on me!  I was starting to research the lsof command, as well as /proc/pid to see if there is any open file information to be used. I found a [_[COLOR="Blue"]fairly long writeup on the /proc file[/COLOR]_]("http://www.cyberciti.biz/files/linux-kernel/Documentation/filesystems/proc.txt") system and a [_[COLOR="Blue"]very long man page on lsof[/COLOR]_]("http://linux.die.net/man/8/lsof").  It merits lookiing into and I will follow up on those. Looking at the [_[COLOR="Blue"]man page for debugfs[/COLOR]_]("http://linux.die.net/man/8/debugfs"), I don't see any options that will help me with an in-memory structure like open inodes.  Still, that's at a first glance.

Thanks - I'll be testing these options next time I boot Ubuntu.

---

### Post by haqking on 2011-08-07
> **rpaskudniak said:**
> Ah!  Someone has taken a crack at at it.  Thank you, haqking!

Point 1: As you can see, I had already obviated the possibility of using _**find**_ for this purpose since my problem involves the lack of a file name for the inum and *find* depends on having an inum, even if I had done the search by inum.

debugfs? That's a new one on me!  I was starting to research the lsof command, as well as /proc/pid to see if there is any open file information to be used. I found a [_[COLOR=Blue]fairly long writeup on the /proc file[/COLOR]_]("http://www.cyberciti.biz/files/linux-kernel/Documentation/filesystems/proc.txt") system and a [_[COLOR=Blue]very long man page on lsof[/COLOR]_]("http://linux.die.net/man/8/lsof").  It merits lookiing into and I will follow up on those. Looking at the [_[COLOR=Blue]man page for debugfs[/COLOR]_]("http://linux.die.net/man/8/debugfs"), I don't see any options that will help me with an in-memory structure like open inodes.  Still, that's at a first glance.

Thanks - I'll be testing these options next time I boot Ubuntu.

ok so another stab at it, i think i understand what you are asking, but it is late ;-)

lsof will show open files (i think link or not) as it does not show just data or directory files.  So i am wandering if this can be used to achieve your goal with a few combinations of switches ?

---

### Post by haqking on 2011-08-07
ok so think this is what you are after:

ils

see here:
[http://manpages.ubuntu.com/manpages/natty/man1/ils-sleuthkit.1.html](http://manpages.ubuntu.com/manpages/natty/man1/ils-sleuthkit.1.html)

with -O or -p i think is what you are after

---

### Post by rpaskudniak on 2011-08-08
Y'all did it again!  By not providing an answer you have annoyed me into activity and I did find what I needed, at least for Ubuntu/Debian.

I see that lsof has more options than fleas on a camel.  However, with no options and just grep, I was able to isolate the deleted file.  I edited a file name junk.  When I do an ls
-al in that directory, I see:
```
rasputin@maxwell:~/scratch$ ls -alt|head
total 32
-rw-r--r--  1 rasputin users 12288 2011-08-07 23:55 .junk.swp
-rw-r--r--  1 rasputin users   766 2011-08-07 23:55 junk

```
In another window I did```
rm .junk.swp
```. The I ran the following lsof command:```
$ lsof |grep rasputin | grep REG | grep junk
``` I expected to get no lines from this; I
would have then looked for it by inode number, obtained from a previous ls -ial.  But here's what I got:
```
vi        5934        rasputin    9u      REG                8,5    12288     590899 /home/rasputin/scratch/.junk.swp (deleted)
```

It had kept the name, although after the rm it no longer appeared an the ls listing.

Going back to my original problem, the solution would have been to run a few successive lsof commands, grep'ing for (deleted), then note any file that seems to be growing out of
control.  Now kill the pid in that line (in this case, 5934) and the file should vanish in short order.

The reason I could not do that in my original case was that there were many instances of that program running.  I would have neded to kill the correct one, the rogue; I could not
simply kill them all; this was a production host!  (And I didn't then know about lsof!)

Again, Thanks, Haqking.  It was a worthwhile effort.  But the man page for ils is incomprehensible and from what little I see of it, seems to not pertain to the issue I was raising.

---

### Post by haqking on 2011-08-08
> **rpaskudniak said:**
> Y'all did it again!  By not providing an answer you have annoyed me into activity and I did find what I needed, at least for Ubuntu/Debian.

I see that lsof has more options than fleas on a camel.  However, with no options and just grep, I was able to isolate the deleted file.  I edited a file name junk.  When I do an ls
-al in that directory, I see:
```
rasputin@maxwell:~/scratch$ ls -alt|head
total 32
-rw-r--r--  1 rasputin users 12288 2011-08-07 23:55 .junk.swp
-rw-r--r--  1 rasputin users   766 2011-08-07 23:55 junk

```In another window I did```
rm .junk.swp
```. The I ran the following lsof command:```
$ lsof |grep rasputin | grep REG | grep junk
``` I expected to get no lines from this; I
would have then looked for it by inode number, obtained from a previous ls -ial.  But here's what I got:
```
vi        5934        rasputin    9u      REG                8,5    12288     590899 /home/rasputin/scratch/.junk.swp (deleted)
```It had kept the name, although after the rm it no longer appeared an the ls listing.

Going back to my original problem, the solution would have been to run a few successive lsof commands, grep'ing for (deleted), then note any file that seems to be growing out of
control.  Now kill the pid in that line (in this case, 5934) and the file should vanish in short order.

The reason I could not do that in my original case was that there were many instances of that program running.  I would have neded to kill the correct one, the rogue; I could not
simply kill them all; this was a production host!  (And I didn't then know about lsof!)

Again, Thanks, Haqking.  It was a worthwhile effort.  But the man page for ils is incomprehensible and from what little I see of it, seems to not pertain to the issue I was raising.

ok well you got it sorted, though i provided lsof above ^

also the ils shows -O for orphan inodes which are inodes being used even after file being deleted which is what you wanted correct ?

anyways you got it sorted, cool.

---

