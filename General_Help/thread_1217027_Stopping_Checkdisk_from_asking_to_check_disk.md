---
title: "Stopping Checkdisk from asking to check disk"
date: 2009-07-19
forum: General Help
---

### Post by kehon on 2009-07-19
i'm on ubuntu most of the time but i have windows in another partition because ubuntu is encrypted but what i want to know is how can i stop windows from asking to check the disk everytime i start windows up because if i dont press a key in a certain time (which i normally start it up from grub and walk away for a second) then it will start scanning and i have to restart windows with power button and wait 

i think there is a flag or something and there should be a command so that it will be stopped but i'm not sure 

also is there a way to mount ext on windows with read/write support that works because i like the ext3 filesystem

---

### Post by jerome1232 on 2009-07-19
Just let it run through the disk check once and it won't keep asking you.

---

### Post by kehon on 2009-07-19
> **jerome1232 said:**
> Just let it run through the disk check once and it won't keep asking you.

i had added this to post ealier but removed because i felt it was to long 

last time i messed with partitions like i did this time and let windows do a disk check i lost alot of data including programming stuff it messed up the mft completly so no scanning for windows and ubuntu for that matter either cause i dont want any data loss when the partition works just fine from what happend last time i've learned if it aint broke don't let windows touch it or it will be broke worse than you can imagine

---

### Post by 3rdalbum on 2009-07-19
Oh my god, whatever you do DO NOT hard-reset any computer when it is conducting a filesystem check!

If you run the checkdisk through once it should stop asking; it tends to run after you resize the Windows partition and I'd highly recommend you let it so you can be sure that the partitioning has worked well.

EDIT: You won't lose data by having Checkdisk run - you made a backup before installing Ubuntu. You did, didn't you?

I have "lost data" by running disk checking utilities before; this happens sometimes when the filesystem does not accurately represent the contents of the disk (i.e. the filesystem is corrupted). You might have to restore a couple of files from your backup, but it prevents your whole filesystem from collapsing two months down the track and losing the last two months worth of work.

If you want to persist in stopping disk checking, you'll need to find a Windows forum and some people who don't mind giving you risky information. I don't know how to stop Checkdisk in Windows. I know how to stop fsck in Linux but I'm simply not going to give out information that plays Russian Roulette with your data.

---

### Post by kehon on 2009-07-19
nope not letting it run because it screwed up big time last time not going thru that again and the check disk had just started and was only scanning so i hard reset it

---

### Post by lisati on 2009-07-19
[SIZE="5"]Make a backup of your data a.s.a.p.!!!!!!![/SIZE] Then you can start looking at options for fixing whatever has gone wrong.

---

