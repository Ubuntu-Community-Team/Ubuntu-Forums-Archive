---
title: "I/O erros and crashes, can't write but can read"
date: 2011-04-08
forum: General Help
---

### Post by Lucky75 on 2011-04-08
Hey all,

Recently my Ubuntu system decided to crash. Sometimes the mouse freezes, sometimes I just can't open anything, and other times I can access the terminal but can't write.

I can open files as read only both in my /home partition and in /var/log, but I can't write at all.

Sometimes I get Bash: input/output error. I *can*  "ls /proc", if that makes any difference. I find that if I reboot, the problem goes away for a few minutes and then reoccurs. 

I can read/write to my other (windows) drive, although when I did a chkdsk in win7, I get a "An index entry from index $0 of file 25 is incorrect" message.

Any suggestions? Is the disk failing? Just a few bad sectors? Maybe the filesystem is corrupt? Why can I read but not write?

Thanks!

---

### Post by earthpigg on 2011-04-08
1) are any of these partitions over 95% full?
in a terminal...
```
df -Th
```

2) *is* the hard drive failing?
system -> administration -> disk utility

---

### Post by Lucky75 on 2011-04-08
My /home partition is over 95% full (around 8GB left), but root isn't. I can't even "su" though. I couldn't really do a disk check with the utility since the drives were mounted and I don't currently have a spare disc to burn a liveCD :(

---

### Post by earthpigg on 2011-04-08
there ya go :)

linux filesystems are generally stable, give you clear warnings when things are about to go wrong, work lightning fast, and do all of that without needing to be defragmented.

everything has a price, though. the downside is that once a partition is ~95% full, things stop working well. this is your 'clear warning' i noted above. 

only root can fill a partition past that magic 95% mark, and even then it should only be doing so for logfiles and similar - things get wonky otherwise.

my suggested solution: boot from a LiveCD, access your home partition, and either delete or move things. performance starts degrading at around the 90% full mark, so i suggest shooting for 85%. 

i do ***not*** suggest trying to resize a partition that is over 95% full.

yes, this 'waste' is frustrating on huge hard drives wherein 5 or 10% can represent dozens of gigabytes. the price we pay for stability and reliability - i believe that absolutely none of your data is actually damaged or lost at present. contrast that with a system wherein you get absolutely no warnings, and suddenly everything is permanently lost.

---

### Post by Lucky75 on 2011-04-08
But why would commands such as "su" not work? That has nothing to do with my /home directory, does it?

---

### Post by earthpigg on 2011-04-09
"su" by itself doesn't work on any perfectly functional ubuntu system, because there is no root password.

```
[chris: ~]$ su
Password: 
su: Authentication failure
```

there is no correct password.

see my post above. until all partitions in use are well under 95% full, things will be broken. I explained why above. Note that I am not asking you to *like* my answer.

---

### Post by Lucky75 on 2011-04-09
I'll give it a try, thanks. I managed to free up 45 GB from a 400GB partition, although I'm currently in the process of making a backup so I can't reboot yet.

I experienced some odd behaviour though. While I was on my windows 7 drive, I was accessing ext4, so I assume I created a lock. For some reason windows crashed, and I wasn't able to boot at all, even to a live CD. It would POST, then display both drives, but it would never load grub (I assume because grub is on my linux drive?). I couldn't even get to the boot menu, so I had to unplug my linux drive, THEN boot from the liveCD, and then re-mount the drive in order to even get into the liveCD.

Could that still have been caused by a partition being full? Or am I running into other hardware issues?

Setup:

disk sda:

- 400GB home partition (was >95% full)
- 10GB swap
- ~50 GB root partition (10.10 linux) (still ~30GB space free)
- Pretty sure it boots from this disk

disk sdb:

- 100GB system partition (win 7) (~50GB free)
- 400GB data partition ( ~60GB free)

---

### Post by earthpigg on 2011-04-09
at that level of complexity without having hands-on, it wouldn't be ethical to provide a hypothesis. 

above all else, at this point, i would prioritize backing up vital data. i have no specific reason to believe any of it is in danger, but better safe then sorry.

when you reinstall, look into simplifying your setup.

first hard drive with 3 partitions:
1) windows. whatever size. (install windows first, on an appropriately-sized partition)
2) linux / (root). 20 gb.
3) linux /home.

second hard drive with 1 single partition.
1) multimedia. (i'm assuming movies/music is what is taking up the better part of one full tb.) if you are in ubuntu's file manager and bookmark -> add bookmark, it will appear under "places".

---

### Post by Lucky75 on 2011-04-14
Hmm...looks like my linux drive is DOA. I can mount it and copy files from it, but i can't seem to write to it. In fact, I can't even seem to boot with it. Not only that, but I cannot even access the boot menu/bios with that drive connected. Is that because of a bad boot sector or something? Unplugging the drive allows me to boot into windows using my other drive almost immediately.

---

### Post by Lucky75 on 2011-04-15
any suggestions? Thanks :)

---

### Post by earthpigg on 2011-04-15
at this point, in your shoes:

copy vital data off of it

remove windows hard drive, replace with ubuntu hard drive

boot from live cd

reinstall ubuntu

---

