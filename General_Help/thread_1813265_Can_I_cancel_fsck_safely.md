---
title: "Can I cancel fsck safely?"
date: 2011-07-27
forum: General Help
---

### Post by nsk7even on 2011-07-27
Hello,

due to an unbelievably concentrated combination of rare circumstances my main system is running a fsck on my main data partition of 1.6 TiB (1.4 TiB used) since 2 days now.

Can I cancel this or will it make things worse?

The Story:
[LIST]
[*]My X freezed due to whatever reason while gparted was shrinking this partition from the beginning
[*]I then checked via ssh that gparted still was running - it was
[*]After work I got no ssh connection anymore
[*]Did reboot via SysRq REISUB
[*]Everything booted up as usual and first I was happy
[*]But then I noticed that at least one directory was lost
[*]My main data was there so I did a backup
[*]Since the missing directory was only containing installed program data I thought everything is fine and I proceeded to work as usual INCLUDING writing additional data on this partition
[*]After next reboot fsck warned of corrupted partition
[*]I decided to let fsck do the check for maybe saving me the time to reinstall those programs
[*]At that time I forgot the newly written data to this partition which had no backup until now (digicam photos and videos)
[/LIST]

What do you think, does fsck make things good or bad just now?
Does it correct all wrong entries with respecting the new data?
Or maybe it undoes all the gparted works now because maybe gparted was not able to cleanly close its modifications?

Any advises or experiences appreciated..

---

### Post by seawolf167 on 2011-07-27
fsck is set to automatically scan and check every 30 boots or if a problem has been detected.

I personally would let it finish, though if you want to stop it, I would highly suggest immediately imaging your system with something like [Clonezilla ]("http://www.clonezilla.org")in case you end up needing to do a recover, then booting back up and starting a fresh [fsck ]("https://help.ubuntu.com/community/SystemAdministration/Fsck")disk check or seeing if you can login and maybe check your syslog messages.

---

### Post by bodhi.zazen on 2011-07-27
> **nsk7even said:**
> due to an unbelievably concentrated combination of rare circumstances my main system is running a fsck on my main data partition of 1.6 TiB (1.4 TiB used) since 2 days now.

2 days is a long time. I would boot a live CD and run fsck manually to see what the problem may be.

Better to fix the problem, or if that is not possible, back up your data and re-format.

---

### Post by nsk7even on 2011-07-27
Thank you for your answer.

So fsck can proceed later when I interrupt it now?

The problem is, I can not read the output because it is scrolling too fast on the screen.
Therefore I can not tell what progress it is and how long it possibly will need to finish...

At the beginning it prints something like "Inode 744763?? ...."
Can I estimate the progress based on this number?

---

### Post by nsk7even on 2011-07-27
Ok, found out via Google that I can multiply the Inode Number with the Inode Size to get the number of Bytes.

Now the magical question: what would be the standard Inode size for a 1.6 TiB Ext4 partition created by Gparted or Palimpsest?
Which one I can not remember since I use both :/

---

### Post by seawolf167 on 2011-07-27
> **nsk7even said:**
> So fsck can proceed later when I interrupt it now?

You can just re-run it from a Ubuntu LiveCD terminal no problems. See the fsck link I posted earlier for a how-to.

> **nsk7even said:**
> At the beginning it prints something like "Inode 744763?? ...."
Can I estimate the progress based on this number?

Not unless you are the drive manufacturer or have a bunch of info available to you on the drive specs.

---

### Post by seawolf167 on 2011-07-27
> **nsk7even said:**
> Ok, found out via Google that I can multiply the Inode Number with the Inode Size to get the number of Bytes.

Now the magical question: what would be the standard Inode size for a 1.6 TiB Ext4 partition created by Gparted or Palimpsest?
Which one I can not remember since I use both :/

Default inode sizes:
128 bytes for ext3 format
256 bytes for ext4 format

---

### Post by nsk7even on 2011-07-27
OK thank you for those informations!

Assuming 256 bytes inode size and me reading the inode number correctly I calculated the progress to be at 17,7 GiB which means it would take another 78 days to complete. I am too impatient for that ;)

Last question:
This is not my root, boot or other partition vital to the system - would it harm to cancel this now and then proceed normal bootup to finally start fsck from the running system afterwards?
Except the fstab automount there should be not much difference to a live cd or is there anything evil I forgot?

---

### Post by nsk7even on 2011-07-27
Something is wrong in my calculation ... just compared with my 2.05 TiB ext3 partition on my server that has an inode size of 256 as well.

nsk@server7even3:~$ sudo tune2fs -l /dev/md127 | grep Inode
Inode count:              137363456
Inodes per group:         8192
Inode blocks per group:   512
Inode size:	          256

Comparing roughly the inode count, my main system passed the 50% a while ago, so my simple formula "inode count * inode size = bytes" is wrong ... I will do a little more Googling, maybe I have to respect the other inode values as well - maybe they are not written there because they look so beautiful... :D :D

---

### Post by seawolf167 on 2011-07-27
You might just want to check to ensure the scrolling text doesn't indicate that it is repairing the file system and restart into a Live environment to check the drive's S.M.A.R.T. status and do a (hopefully quick) fsck from there.

---

### Post by nsk7even on 2011-07-27
I think it does repairs - it is telling about something is too big and the last word is "repair", followed by question mark and then there seems to be the automated yes.
Sometimes a different structure of lines appear, maybe telling about some "bad" something...

I think I will wait another day. If those numbers posted out of my server's output are comparable in any way it should have been finished in at least this additional day.

In parallel I will burn this Clonezilla cd to be prepared.

Thanks for all the help!

---

### Post by seawolf167 on 2011-07-27
No problem - let us know what ends up happening!

---

### Post by nsk7even on 2011-07-27
Hey, technically I got an error, but concerning the data I can report success!

What happened:
- suddenly fsck aborted with a message alike "no memory left"
- it was not clear to me whether this relates to harddisk space or system memory
- I got three options: Ignore, Skip mounting and manually fix
- chosed skip and the system proceeded booting
- after a long time of thinking (especially from where I can spawn 1.4 TiB of free space :D ) [this wiki]("http://wiki.ubuntuusers.de/Datenrettung") gave me the idea to mount the partition read-only
- did that and *wow* everything is there as it was before (the missing directory was still missing), but most importantly the last digicam imports are vital!
- something weird is going on there as one directory of those digicam folder structures has an endless loop letting baobab tell me that those are 536,6 GiB of data :D but I can open the pictures, that is the most important part!

So ... I will do immediate backup of those new data which I haven't backed up until now and then take a look at fsck again.

All in all I have to state that this filesystem seems really really robust to me, thinking back to NTFS times everything would have been gone now and I would be struggling with data rescue tools.

---

### Post by seawolf167 on 2011-07-27
> **nsk7even said:**
> So ... I will do immediate backup of those new data which I haven't backed up until now and then take a look at fsck again.


Sounds like a good plan :)

Glad the entire filesystem wasn't corrupt or anything!

---

### Post by nsk7even on 2011-07-28
Little update:
fsck denied to run with the -a option because it detected "unexpected inconsistency".
Started it without therefore and it did not took much time to begin asking me difficult questions whether to repair this or that (e. g. restore group descriptors, correct inode root, ..)
After some googling I decided to allow repairs and answered with yes.

Everything looked good and fsck started phase 1 (inode checking). At approx. 40% a new type of question occurred:
Inode <number> should not have EOFBLOCKS_FL set (size 0, lblk -1) Clean<y>?

Bad thing about that is that it is repeating and repeating and repeating. I already tried to cancel and restart with -a option, but fsck denied this again.
Good part on that is that the inode number proceeds, so I can cancel and resume fsck without repeating the whole stuff from the beginning.

I constructed a little stone and my glass on the "j" key (this is yes for germans.. ;) ) and this runs for approx. 6 hours now ..... just as I am writing those words there is a change:
There were some other inode errors (all were autofixed by my stone) and then fsck stopped with the known "Memory allocation failed" error again.

Now I restarted fsck and the story proceeds were it aborted. Tried -a again with a little hope that it works this time, but it does not. So my stone has to engage again...

---

### Post by nsk7even on 2011-07-30
Ok, some advised to others in similar situations:

- If you have a partition of that size, don't try to repair it because it takes nearly forever. Instead, use your backups and create the partition from scratch

- Don't use Gparted for fixing partition errors. It may have been by accident, but now my partition is not mountable anymore. Additionally Gparted stopped with the message that there was an error, but not telling which one. Saving the log from within the Gparted GUI let it work with 100% CPU on one core for a whole day and wasn't finished then .... that is silly.

- If you encounter the same problem as me that fsck and e2fsck denies to run with the -a/-p option because there are "unexpected inconsistencies", but when running manually they will ask you questions for nearly forever, cancel that. Try using the -y option of e2fsck instead as this answers all the questions much faster automatically.

Working for a week now on this partition problem, it would be most reasonable to re-format and re-import the backup data as mentioned above.

But - being addicted to technics - I wanna know now if it is possible to completely restore from such an error. ;-)

---

