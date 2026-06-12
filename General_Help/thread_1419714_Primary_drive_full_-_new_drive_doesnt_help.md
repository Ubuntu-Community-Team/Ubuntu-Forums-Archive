---
title: "Primary drive full - new drive doesnt help"
date: 2010-03-02
forum: General Help
---

### Post by tiggsy on 2010-03-02
I am using an old computer while my main beast is awaiting repair.

The problem is that the primary disk on this is so full I can't even do regular updates, have to load firefox with sudo, and so on.

So I just bought and installed a second slave IDE drive. I tried to download Karmic onto it. But I get the following message:

```
There is not enough room on the disc to save /tmp/vFW3OuPe.iso.part.

Remove unnecessary files from the disc and try again, or try saving in a different location
```

Is there a solution?

---

### Post by bobcollard on 2010-03-02
> **tiggsy said:**
> I am using an old computer while my main beast is awaiting repair.

The problem is that the primary disk on this is so full I can't even do regular updates, have to load firefox with sudo, and so on.

So I just bought and installed a second slave IDE drive. I tried to download Karmic onto it. But I get the following message:

```
There is not enough room on the disc to save /tmp/vFW3OuPe.iso.part.

Remove unnecessary files from the disc and try again, or try saving in a different location
```Is there a solution?
You could partition the second HD and move a lot of files there, or you might make it the Master and then install the Ubuntu Karmic.  Either way, the installer is looking for room on the Master to unpack it's files to install.  Minimum requirements is 2GB to install.

---

### Post by FinalShot on 2010-03-02
I think it's using the temp directory on your first full hdd, but it's full. Maybe moves some files to the 2nd hdd enough space to download ubuntu.

---

### Post by dabl on 2010-03-02
First concern would be, are you absolutely certain of your disk IDs?  In other words, in the BIOS is one the "master" and one the "slave"?  It could be trying to save the ISO to the drive that is already too full.

If you certain of the ID of the secondary drive, then I would advise using GParted, and partition it and format the partition ext3 or ext4 (I assume there's no data on that drive).  Then you have to mount it -- lots of threads on the forum on how to do that.

---

### Post by tiggsy on 2010-03-03
I solved the problem of saving the iso file. What i did was change the options on firefox to ask every time I download, instead of automatically saving (even though I had set this to save to the new disk, i was still getting the message). Then I went to the alternative download spaces and used rightclick to dl.

Now I can use it for data storage, which is fine. But I still can't update ubuntu, or even use synaptic. When I try to get into synaptic, I get this message:
```
Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file
```

Also, and more worrying even, is that I'm getting intermittent startup problems. When I turn on the computer, there seems to be a better than 50% chance that the splash screen will freeze for no apparent reason. Even if I go away and do something else to give it a chance, it never recovers from this. But if i force shutdown with the big button, then start again, it might be ok - or it might freeze again. This occurs even first thing in the morning when it's cold, so can't be caused by overheating, as I suspected.

---

### Post by bobcollard on 2010-03-03
Secondary drive must be mounted for Firefox to find it.
To run Synaptic as root you might try "sudo synaptic" (without quotes) in terminal.    Not sure why you don't have a login screen before opening synaptic.  That's how most of us get Root privileges.

---

### Post by tiggsy on 2010-03-03
The secondary drive is mounted, which is how i am managing to save stuff on it.

The issue with not getting into synaptic is explained in the message - there isn't enough room for it to update the file where it stores usage. There is ZERO space on the main disk.

And i can't find anything that can be deleted. What data there was on the first disk (minimal) has been moved to the secondary, deleted, and the Deleted items folder emptied.

---

### Post by bobcollard on 2010-03-03
I am not experienced enough, but, a suggestion.  Could you run the two disks in Raid?  That would make them one disk virtually and improve your size problems.

---

### Post by pmooney78 on 2010-03-03
Your basic problem is that you have zero storage on your primary hard disk. You have to solve this one way or another before you can do much else. There are a couple of options ...

1. Just reinstall Ubuntu to the larger disk. I hate to recommend this, but if you're in a big hurry to get a normally working system going again, it might be your fastest option, depending on your level of expertise. You may wind up needing to do this eventually anyway. Make sure you back up your home folder and any other important data on the drive. 

2. Look for programs you can uninstall. (Nothing? Really? NOTHING? Think about it for a minute ...) That should free up SOME space.

3. Empty out your temp folder. First close down everything you can possibly close so no running programs are using it, then

```

sudo rm -R /tmp/*

```

from a terminal should do it, but leave the folder existent. You might then want to modify your /etc/fstab file so that it mounts as /tmp, which would give you some free space to play with in your temporary.

4. Think again about reinstalling the operating system to the larger hard drive. Having your operating system on a single hard drive is likely to yield better performance than spreading it across multiple drives unless you really know what you're doing. If you're out of hard drive space, then (chances are) you need a bigger hard drive to continue using your computer in the way that you're accustomed to doing so. 

Hope some of that helps.

---

### Post by tiggsy on 2010-03-03
I uninstalled openoffice - I now have 12% free, which is a definite improvement. I've also copied .mozilla from my home folder to the new disk, so I could reinstall on the old disk, if only the Windows bit was on one end or the other - there are things on there I need to keep, which will not run in linux, and i don't find the virtualbox solution much use, given that you can't port data in and out - what's the point of that?

This is what I get when I fdisk the old drive. I'm a bit confused as to why I have two swap files, and according to the System Monitor, the drive I'm using is sda7, given the size of which (3.2Gb) my problems are not impossible to understand.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4845    38917431    7  HPFS/NTFS
/dev/sda2            4846        9729    39230730    f  W95 Ext'd (LBA)
/dev/sda5            4846        8768    31511466   82  Linux swap / Solaris
/dev/sda6            9220        9729     4096543+   b  W95 FAT32
/dev/sda7            8769        9192     3405748+  83  Linux
/dev/sda8            9193        9219      216846   82  Linux swap / Solaris

Is it the case that if I use gparted, all the data will be destroyed? If so, I can't use it on either disk. There's not enough room on sda to put the .iso, and I can't lose the windows stuff. This is beginning to work like a maze in an old text adventure, where you keep trying new avenues and never get out.

Another problem is that when I put a known good Hardy disk in the drive and try to either boot or even just run linux from it, I get infinite SQUASHFS errors. I guess this might be because of the lack of space, and I haven't tried it since I got rid of Open Office.

I will try to burn the karmic image. In the worst case i have a genuine Ubuntu gutsy cd. (But I hate doing multiple major updates, it just takes so long!)

---

### Post by psusi on 2010-03-03
Wow you have a very messed up partition scheme there.  You only have 3 gigs for your root fs, but 16 gigs for swap.  If you use gptarted to DELETE a partition, then yes, everything in it is gone.  It can also resize and move them though, and that does not destroy data ( unless something goes wrong ).

It sounds like you need to just reinstall.  I'd suggest just installing to the new hd all by itself, get the system working, then plug in the old drive and pull off any data you want to save.

---

### Post by tiggsy on 2010-03-03
OK. I have almost solved this.

Neither the hardy disk (which was used to set this computer up, so i know it's ok) nor the genuine Ubuntu Gutsy Live cd would boot. So it appeared i was stuck. I decided to try one last thing:

1. I managed to burn a cd with the iso. To achieve that, I had to specify that the temp file was created on the new virtually empty disk. The realization that this was necessary was not helped by the fact that it kept saying that "the" disk ws full, so I kept trying new cds...

2. I booted from the new karmic disk successfully and went to System->Admin->Gparted, where I removed the sda8 swap file, reduced the size of the sda5 swap file and increased the ext3 partition to around 30gb.

3. I did a clean install of karmic, manually selecting the 2 partitions I just sorted out.

And now it's working.

Only one problem. How do I retrieve my bookmarks, so on, for Firefox> I carefully backed up the .mozilla folder which contains all this stuff (i believe), but deleting the new .default folder makes firefox unusable, even though the old one is there.

---

### Post by tiggsy on 2010-03-03
Right, in case anybody has to go through a similar saga, I'll just finish off the final fix.

To get your old profile to be the one that's used, you just need to [go to your home folder, select View Hidden Files to find the folder] edit .mozilla/firefox/profiles.ini to put your old profile name in:

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=YOURPROFILEID.default
Default=1

```

---

### Post by ben2talk on 2010-11-06
The way I managed this problem was to boot a liveCD, then shrink the first (XP) partition from 60 to 50GB, then expand the root partition to fill the hole (20 to 30GB and move left).

Using the liveCD is the way to go here I think.

---

