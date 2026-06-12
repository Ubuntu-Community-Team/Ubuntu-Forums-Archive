---
title: "MediaMonkey on VirtualBox Windows guest"
date: 2009-08-31
forum: General Help
---

### Post by Martin Rabson on 2009-08-31
Wanted to post this for those trying Ubuntu but missing their Monkey!

I am using MediaMonkey on an XP guest within VirtualBox on Ubuntu host.

My set-up. 
Ubuntu 9.04 (my HOST OS) - Sun VirtualBox 3.0.4 with a Virtual Machine (my GUEST OS) XP 64 bit. VirtualBox Guest Additions installed. Link follows to solve my problem to installing Guest Additions.
-[http://ubuntuforums.org/showpost.php...27&postcount=7](http://ubuntuforums.org/showpost.php...27&postcount=7) ([http://ubuntuforums.org/showpost.php?p=3737927&postcount=7](http://ubuntuforums.org/showpost.php?p=3737927&postcount=7))

My computer is an Intel that has virtualisation capability, and is enabled in the BIOS of the motherboard.

1st HDD [OSs] = 80gb with XP 1st partition and Ubuntu installed after the XPs NTFS partition at end of drive.
2nd HDD [Data] = 750(ish) gb 2x partitions both NTFS. All my music files as FLAC+jpg on 2nd partition. This was the source for the Monkey while on the native running XP OS install.
MediaMonkey is not accessing any Files/Folders on Ubuntu 'per say' just caching Images and MediaMonkey settings within the XP Virtual machine.

I am running a new installed XP Virtual Machine and have installed MediaMonkey. Within VirtualBox [Shared Folder] set-up I set a [Machine Folder] pointing to the Music Folder on my second NTFS HDD. 
I made the share name short (no spaces or special characters) or the [OK] button remained greyed out! The shared folder then showed in XP in [My Network places] and then [VirtualBox Shared Folders]. I mapped this folder in XP and it is this the Monkey stares at :razz:
Link follows for solution to greyed out [OK] button in VirtualBox Folder Share set-up dialogue.
-[http://forums.virtualbox.org/viewtopic.php?f=6&t=20184#p87427](http://forums.virtualbox.org/viewtopic.php?f=6&t=20184#p87427)

I could then within MediaMonkey [Add/Rescan Tracks to the library...], pointing to my new shared Music folder on the Original HDD I used in native running XP with MediaMonkey. It was slower at scanning the tracks, 93.2 gb of FLAC and image jpgs.
But it works and the music is playing okay.
I am still looking into some sound anomalies regarding the Smooth Pause/Seek/Stop, cracking scratching so I have these disabled. Also the XP windows system sounds cause the same noises so system sound are off too. So something needs changing. There are lots of threads with references to this sound issue, it is a known problem.

So 'in short' yes there are other music players in Linux, but I wanted MediaMonkey, I am used to it and had everything set-up in XP as I wanted. So now I have the chance to learn about Linux Ubuntu while being serenaded by the monkey.
I have my cake, and I am eating it too!!

---

### Post by DFlame on 2009-08-31
Compatibility seems to be improving with [WINE](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15795) too.

EDIT - Those are old test results. Wonder if it works even better now...

---

### Post by Martin Rabson on 2009-09-01
As far as I can tell, MediaMonkey on this VirtualBox XP machine is performing the same as it was on my native windows xp.
I haven't found or noticed anything odd yet. I'll post anything here if I do.
And I will look at trying Wine as well.


After further playing>

64 bit Ubuntu 9.04 Host with a 64 bit XP Guest was the cause of my sound anomalies.
Installed 32 bit XP guest and running on Ubuntu 64 is fine, no sound issues at all so far, system sounds or music player.

---

### Post by excetara2 on 2010-10-21
Did you ever try connecting to an ipod through the monkey on virtual box??

Thanks,
Cheers

---

