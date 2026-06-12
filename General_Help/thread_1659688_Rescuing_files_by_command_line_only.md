---
title: "Rescuing files by command line only"
date: 2011-01-04
forum: General Help
---

### Post by raysa on 2011-01-04
I have a laptop with Ubuntu 10.04 which appears to be completely wrecked. Even in recovery mode I can't get any GUI. The only access I can get is via command line, which with my limited knowledge of cd and ls commands shows me that the home directory is OK and all the data files present.

How can I get the data files off this machine, eg by copying them to a usb stick, or maybe by copying them to the Windows partition (which still works OK)?

Thanks, Ray

---

### Post by KJ KJ KJ on 2011-01-04
You can do this. 

First, do you know where all your data is, and how much data there is?

Run the command 'df -h' and post what you see. It should tell how much free space you have on various disk partitions.

(BTW, be cautious when people tell you to type things)

---

### Post by Verbeck on 2011-01-04
first mount the usb drive / windows partition, (replace /dev/sdXx with the actual partition. you can find it using[FONT=Courier New] [/FONT]*[FONT=Courier New]sudo blkid -c /dev/null[/FONT] *or* [FONT=Courier New]suddo fdisk -l[/FONT]* (lower case L))
```
sudo mkdir /media/Data
sudo mount /dev/sd**Xx **/media/Data
```the copy the stuff
```
cp -r /home/directoryname /media/Data
```then check whether it is copied
```
ls -la /media/Data/directoryname
```

---

### Post by raysa on 2011-01-04
Thanks. It shows /dev/sda6 (which is the main Linux partition) but says it is completely full - size 53G, used 53G, available 0. (Curious - there was plenty of space before the crash).
Then there are several 'filsystems' identified as 'none', which have size 493M each and very little used.
There is no mention of /dev/sda1 which is the Windows partition (where there is about 30G of spare space), nor of a 4G usb disk which is plugged in.
I seem to remember the Documents directory that I want to save is just a handful of Gb.

---

### Post by KJ KJ KJ on 2011-01-04
Verbeck's suggestion works, but if you copy from Linux to a Windows partition of a FAT formatted USB stick, all the permissions become messed up, and (I may be wrong on the second point) the dates aren't preserved.

I'd have suggested using 'tar' to preserve permissions and dates, long filenames and so forth.

---

### Post by aysiu on 2011-01-04
How about booting a live CD, mounting your drive (go to Places and then click on your drive size), and then copying the files off to an external hard drive *graphically* without the command line?

Note: you will have to Alt-F2 ```
gksudo nautilus
``` to get a graphical root browser, and you may need a root browser, otherwise not necessarily have permission to certain files.

---

### Post by KJ KJ KJ on 2011-01-04
> **raysa said:**
> Thanks. It shows /dev/sda6 (which is the main Linux partition) but says it is completely full - size 53G, used 53G, available 0. (Curious - there was plenty of space before the crash)..

That sounds broken alright! 

Maybe something has created a huge file in '/tmp'?  In general, you can look for big files like this.

find / -size +100M

/ is where the search starts, and it looks for files of 100 Mbyte or more. 

If there is a big file someplace, that may be what stops everything else working because the disk is full.

---

### Post by QLee on 2011-01-04
[QUOTE=raysa]Thanks. It shows /dev/sda6 (which is the main Linux partition) but says it is completely full - size 53G, used 53G, available 0. (Curious - there was plenty of space before the crash)....[/QUOTE]

This is the source of your real problem. You did something to cause your root partition "/" to fill up and thus you can't boot to the system.

As    	KJ KJ KJ has suggested, determine what unnecessary stuff is in your filesystem, a hint could probably be taken by what you were doing when the problem occurred. Very likely you were writing something to a different directory than the one you thought you were writing to, maybe didn't have something mounted that you thought you had mounted. You could look for the stuff from the live CD also, not restricted to command line.

---

### Post by raysa on 2011-01-04
Thanks for all your help, folks. 

I'm succesfully transferring all my stuff with aysiu's suggestion of using the live CD to do it in familiar graphical environment - very neat.

Next I'll try to find the rogue giant file(s), or maybe with all my data safely on another machine I'll give this one a fresh start with 10.10

Thanks again everyone - brilliant forum this!

Ray

---

