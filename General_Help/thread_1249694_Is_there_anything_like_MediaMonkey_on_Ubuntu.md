---
title: "Is there anything like MediaMonkey on Ubuntu?"
date: 2009-08-25
forum: General Help
---

### Post by serenelune on 2009-08-25
I've made the (accidental and complete) switch to Ubuntu when I was trying to merge my windows and Ubuntu partitions, thus deleting both OSes from my computer. While I didn't want this, on the other hand, I had nothing of value and this meant killing Windows. Anyway with that came the loss of Media Monkey. I know they themselves have a guide on how to play it in Ubuntu and I can get everything to pop up, but, whe it comes to playing my music it just scans it. And doesn't play anything. I followed all of the instructions (Install Wine, install Wine Tricks, install the thing for MP3). I just gave up. I've also very recently (A day now) so that probably doesn't help. So I went to look for the next best thing. Exaile. I went to download that from the Exaile site but it told me the key was missing. I've followed the instructions on the site and no luck whatsoever. I've managed to install similar files but not this one. I want to install the tar.gz but honestly that's a bit too complicated since I've heard you have to compile and I'm not too familiar with that. Can anyone help?

---

### Post by tgeer43 on 2009-08-25
> I can get everything to pop up, but, whe it comes to playing my music it just scans it. And doesn't play anything.Sounds like your music files are located on a drive or partition that is not currently mounted.

I have been known to be wrong, however. :wink:

tgeer

---

### Post by oldos2er on 2009-08-25
To install Exaile, open a terminal and run this command:
```
sudo apt-get update && sudo apt-get install exaile
```

---

### Post by Martin Rabson on 2009-08-31
I am using MediaMonkey on an XP guest within VirtualBox on Ubuntu host.

My set-up. 
Ubuntu 9.04 (my HOST OS) - Sun VirtualBox 3.0.4 with a Virtual Machine (my GUEST OS) XP 64 bit. VirtualBox Guest Additions installed. Link follows to solve my problem to installing Guest Additions.
-[http://ubuntuforums.org/showpost.php...27&postcount=7](http://ubuntuforums.org/showpost.php...27&postcount=7) ([http://ubuntuforums.org/showpost.php?p=3737927&postcount=7](http://ubuntuforums.org/showpost.php?p=3737927&postcount=7))

My computer is an Intel that has virtualisation capability, and is enabled in the BIOS of the motherboard.

1st HDD [OSs] = 80gb with XP 1st partition and Ubuntu installed after the XPs NTFS partition at end of drive.
2nd HDD [Data] = 750(ish) gb 2x partitions both NTFS. All my music files as FLAC+jpg on 2nd partition. This was the source for the Monkey while on the native running XP OS install.
MediaMonkey is not accessing any Files/Folders on Ubuntu 'per say' just caching Images and MediaMonkey settings within the XP Virtual machine.

I am running a new installed XP Virtual Machine and have installed MediaMonkey. Within VirtualBox [Shared Folder] set-up I set a [Machine Folder] pointing to the Music Folder on my second NTFS HDD. 
I made the share name short (no spaces or special characters) or the [OK] button remained greyed out! The shared folder then showed in XP in [My Network places] and then [VirtualBox Shared Folders]. I mapped this folder in XP and it is this the Monkey stares at  :razz:
Link follows for solution to greyed out [OK] button in VirtualBox Folder Share set-up dialogue.
-[http://forums.virtualbox.org/viewtopic.php?f=6&t=20184#p87427](http://forums.virtualbox.org/viewtopic.php?f=6&t=20184#p87427)

I could then within MediaMonkey [Add/Rescan Tracks to the library...], pointing to my new shared Music folder on the Original HDD I used in native running XP with MediaMonkey. It was slower at scanning the tracks, 93.2 gb of FLAC and image jpgs.
But it works and the music is playing okay.
I am still looking into some sound anomalies regarding the Smooth Pause/Seek/Stop, cracking scratching so I have these disabled. Also the XP windows system sounds cause the same noises so system sound are off too. So something needs changing. There are lots of threads with references to this sound issue, it is a known problem.

So 'in short' yes there are other music players in Linux, but I wanted MediaMonkey, I am used to it and had everything set-up in XP as I wanted. So now I have the chance to learn about Linux Ubuntu while being serenaded by the monkey.
I have my cake, and I am eating it too!!

Good Luck!

---

### Post by ad_267 on 2009-08-31
Songbird looks like it would be closer to MediaMonkey, but I havn't ever used MediaMonkey so can't say for sure. Banshee is a pretty good media player too.

You should check out how to install packages on Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

No need to install stuff from the project's website, just use Add/Remove applications in Ubuntu.

---

### Post by fluffman86 on 2009-08-31
I love Banshee.  Smooth and clean interface.  It does podcasts, video, file organization and renaming, iPod and other media player syncing, automatic conversion to the correct filetype for the media player.  

I don't know how it compares to MediaMonkey, but I know I can do everything in Banshee that I could do in iTunes (minus the store).

---

### Post by ad_267 on 2009-09-01
This person thinks [aTunes]("http://www.atunes.org/") is similar to Media Monkey: [http://ubuntuforums.org/showthread.php?t=1255018](http://ubuntuforums.org/showthread.php?t=1255018)

---

### Post by Martin Rabson on 2009-09-01
64 bit Ubuntu 9.04 Host with a 64 bit XP Guest was the cause of my sound anomalies.
Installed 32 bit XP guest and running on Ubuntu 64 is fine, no sound issues at all so far, system sounds or music player.

---

