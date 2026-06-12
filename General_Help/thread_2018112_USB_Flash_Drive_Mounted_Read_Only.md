---
title: "USB Flash Drive Mounted Read Only"
date: 2012-07-06
forum: General Help
---

### Post by svtguy88 on 2012-07-06
I have a 32 GB PNY flash drive that I bought a month or two ago.  It's been working fine, but last night I decided to try and make a bootable USB stick out of it -- which didn't work, but that's another battle for another day.

Anyway, I reformatted the flash drive using Disk Utility, and now it mounts as read only.  Everything I try to copy/paste to it fails, saying the drive is read only.

If I go to the drive's properties, it lists my user as the owner, but any changes I attempt to make to the permissions don't seem to stick.  For example, using the dropdown box to change the group permissions to allow my user's group access to create and delete files doesn't work.  It reverts back to the previous setting.

Anyone?  I appear to be the owner, but I can't write...

---

### Post by svtguy88 on 2012-07-06
I just tried mounting my phone (Android mass storage), and it too is giving me a "read only" error....

---

### Post by LisaBrane on 2012-07-07
What I've written below following "Directions" worked for me.

Moderator: I only began using Linux/Ubuntu a year ago.  I never had a problem with a USB stick becoming unwritable before then.  Since then, it has happened 4 times and after it has, I can't write to the USB stick or delete from it or format it in either Windows or Ubuntu.  I doubt this is a hardware problem.

I have to count my pennies.  I can't afford to throw these things away, even with a "free" operating system.  The cost of my discarded USB sticks will soon outweigh the cost of the Windows upgrade, for crying out loud.

I suspect that Linux can designate an entire drive, an entire partition, or an entire directory as "Read Only." Why it would do that on its own, I don't know. Or why it would be so difficult to change, I don't know.  I do think what is happening is that an entire partition of a one partition drive (in my case at least) is being designated as "Read Only" and the problem needs to be dealt with at that level.  In other words, you can't reformat the drive until you deal with the RO designation for the partition, even if the drive only has one partition.

But I'm not a programmer, either.

DIRECTIONS
As I noted, this worked for me with a Toshiba 16 GB memory stick. I haven't tried it with anything else.  Hopefully it will work with you.

1.  BACKUP.  BACKUP.  BACKUP.  If you have more than one partition, make certain all are backed up.

2.  Open the disk utility.  In Ubuntu, go to the launcher, DASH, and type "Disk Utility" and open the program.

3.  Look on the left side and locate your USB stick.  Click on it.

4.  On the right side you will see two sections.  On top is "Drive" and below it is "Volume".

5.  If you click on "Format Drive", which is what I did all the time, you probably won't be able to format the drive.  I never could.  I also couldn't format the things in Windows or through a terminal.

6.  In the Volumes section you'll see a map of your drive and partitions.  Mine only shows one partition.  I suspect you'll see different colors covering different areas if you have more than one partition, but I don't know.

7.  If you have more than one partition, you may have to click on a particular color in the drive map.  I don't know.  Try at your own risk.  But you may have to do this with all of the partitions to get your drive working properly. I don't know.  I have limited experience.

8.  Click on "Unmount Volume" in the Volumes section.  

9.  Click "Format Volume".  It will ask if you are sure, click yes.

10.  Repeat 7-9 for each partition if more than one.  Or, stop and see if it works with just doing one.  Experiment if you feel like it.

11.  Click on Format Drive in the Drive section above and reformat drive as you prefer.  If you have multiple partitions and only one is a problem, you may not need to reformat the drive.  Again, I don't know.

12.  Click "Mount Volume" in the "Volumes" section.

If it worked, you'll be able to open the drive and see it is clean and it will be writable again.  

Like I said, this worked me for THIS TIME with THIS PARTICULAR DRIVE and ONE PARTITION. I don't know if it will work with other drives, multiple partitions or if this was a fluke.

I'm not going to go buy any more drives to test my theory, either.



Good Luck!!!!

EDIT:  FYI:  This particular flash drive I had the problem with had been made into an emergency Start Up Disk using Startup Disk Creator.  I was using the extra space for video storage.  The problem happened when I was watching a video. The computer froze and I rebooted.  I finished the video and tried to delete it and a couple of other files, but was unable to do so.  I also couldn't write to it (though Deluge bittorrent client continued to download to it!!!).  I rebooted and tried again.  I selected 6 files to delete and couldn't.  I then cut it to three and got those deleted.  I tried the remaining three, but from then on couldn't delete anything or write anything to it.  Though Deluge continued its download.  I assume the file was left "open" for some reason and Deluge finished it, though new torrents couldn't start.

And that is when I started hunting again without success for any help.  Just got lucky monkeying around with Disk Utility.

---

### Post by sudodus on 2012-07-07
1. First try what has already been suggested :-)

2. If no luck, I suggest that you try what I usually do (if possible).

*. But before you start partitioning and formatting: What metnod did you use to make your USB flash drive bootable? If some very special trace is left, it may corrupt normal usage of it.

It seems that you are running Linux with Gnome already, since you have Disk Utility. Then I guess that you have some Ubuntu install drive (CD or USB). Boot a live session from it (even if it is old) and run ***gparted***

Delete any partitions from the USB flash drive and start with a new MBR (MSDOS) partition table.

Make a partition and mark it with the flags for boot and lba. Select a descriptive label.

Format the partition to the FAT32 file system.

Now you should be able to mount the USB drive automatically (with the file browser) and you should get read/write permissions. If that is not the case, maybe the USB flash drive is damaged mechanically or electronically (bricked).

3. But there is still another chance. Wipe and reformat the USB flash drive with a computer running Windows.

---

### Post by svtguy88 on 2012-07-09
Well, my problem is gone, but I'm not totally sure what fixed it, but the drive is now read/write again.

I used Image Writer to make the drive bootable (it's in the repos), although it would not boot.  I'm unsure if this is flash drive, software or BIOS related, but whatever it is, it didn't work.

I reformatted the drive a number of times.  I tried a few formats, but nothing worked.  I tried one last time reformat the whole drive, and went to bed.  When I booted up my system in the morning, the drive mounted...

Whatever, it's working now.

---

