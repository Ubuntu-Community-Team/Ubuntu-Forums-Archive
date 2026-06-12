---
title: "Wine, Win XP, fresh installs, problems."
date: 2010-07-18
forum: General Help
---

### Post by Bampfsnap on 2010-07-18
I installed ubuntu about 3 days ago. It had an error doing the direct install from disc, so it booted me up into the live session version of LTS 10.04. from there I clicked the installer, and just followed it through, and it loaded fine.

At this point its a brand new machine with sata and it asked me to put it into AHCI mode or whatever, so I said yes. 

Today, I didn't uninstall linux, but I tried to load windows xp. I wanted a dual boot scenario in the first place, and since I haven't done much in ubuntu, and made some mistakes with it, I figured I could reset those mistakes and get a dual boot all at once just by loading win xp, and hearing how win XP overwrites linux.

I got win xp loaded. but I had to go to turn off the AHCI for sata in the bios, I set it to native IDE instead, because otherwise windows XP wouldnt find the hard drive.

I went and set it back to AHCI after installing windows. Windows got the blue screen unable to boot error. I figured fine, I'll just keep it as AHCI and reload linux.

I went directly to  linux live since the regular install from disc failed before, and tried to install. I saw the partition of windows, and when I tried to load linux, the disc got about 27% done after the partition junk and getting the installing linux screen, then I got an error that runs like this:

"my cd drive or cd needs to be cleaned, or my hard drive is old, or I need to run the thing at a cooler temp".

I checked the CD with the linux CD boot checker to see if everything was fine, and it said all the data was fine, so I think that means the CD drive is fine as well. I know the HDD isn't old.



Is there benefit to AHCI over native IDE for a single hard drive?
Did attempting to get windows xp installed mess things up?
Why, from the very beginning could I not get the CD to just install directly, and instead it had me go into a live session?
Why was it able to  install the first time, but not now? I have erased all partitions, afaik.

edited: Also, the CD drive in this live session I have going right now is saying "500 gb Hard Disk: 495 Gb filesystem".. but its a CD drive. what?

---

### Post by marshmallow1304 on 2010-07-19
First, if you're dual-booting with XP, leave AHCI mode on IDE.  Ubuntu will handle both and XP chokes on SATA (remember that XP is quite old and SATA is somewhat new).  I think there's a way to add SATA drivers to XP after install, but I don't know if it's worth it.

As for Ubuntu, I get the feeling that the CD is bad, even if the self-check came back clean.  First make sure your download is not corrupted using [winMD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows") or by downloading the iso with a torrent client.  Then burn another copy at the lowest possible speed.

---

### Post by Bampfsnap on 2010-07-19
ok, I switched CD drives to an older one, and it still gets the problem of not installing properly from boot screen, but it did install this time while in the Live session.

Should I worry that it might be corrupt still? could there be problems with it if the CD is corrupt and it installed the OS not all there?

---

