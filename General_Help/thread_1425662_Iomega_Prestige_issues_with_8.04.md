---
title: "Iomega Prestige issues with 8.04"
date: 2010-03-09
forum: General Help
---

### Post by loswr86 on 2010-03-09
Hello all,

I am going to try and recount all the issues I have had and I hope someone has some insight, and if not, there will at least be a record for other users who run into these very odd problems. This is a long post. 

Was given a Iomega Prestige 1 TB Desktop Hard Drive (model # 31837700) as a gift. Out of the box it is formatted with NTFS. I needed it to be usable with both my desktop and my Playstation 3. I run Ubuntu 8.04 for my desktop, and occasionally it would get plugged into my wifes MacBook running Snow Leopard. In order for the drive to work with the PS3 I needed to reformat it to FAT32. This is where it got sticky.

I plugged it into my desktop and fired up gparted from ubuntu. The drive would not mount. Tried rebooting, nothing. So I fired up a gparted live disc rather than running from ubuntu. This did mount the external drive. Ok, so I reformat the entire drive to 1 primary FAT32 partition. I shut everything down and fire up ubuntu again. External HDD visible to ubuntu. However, when I open the HDD up to start adding files, it says I don't have permission. Weird. So I pull up the terminal, and fire up nautilus as root (gksu nautilus). Finally, I have access, but damnit...how do I change the permissions/ownership? Gparted never asked/ nor did I find a setting for ownership when formating. Oh well, I give up and decide to just access as root whenever I need to use it. 

Everything is going smoothly, I add many videos, some music, and some other backup documents and whatnot. Everything is accessible by both the PS3 and the Root user in ubuntu. However, at some point the HDD magically becomes readable/writeable by the user on my desktop, not just root. I did nothing to make this happen. I only know this because I came home and found my wife moving files between the desktop and her Macbook with the HDD, and she has no knowledge of logging in as root. She said she just double clicked the icon on the desktop (for the HDD) and started accessing the HDD. Next time I go to use transfer files as root, the HDD doesn't show up. It does automount and is visible from the desktop, but not nautilus as root. I am befuddled by this for a few days, did a bunch of searching..to no avail. after a few days not using it, I plug it back in and it is back to normal, accessible as root and nothing else. 

So the HDD works as intended (sorta) for a few months. Then one day a couple of weeks ago, I fire it up in ubuntu and everything on the HDD is gone. Well, disappeared is a better description, as there is still 100 gb of space missing on the HDD. Why did this happen? I have no clue, but I cannot find any files, hidden or otherwise, on either ubuntu or PS3. I happened to be working on a friends laptop and installing windows 7 for her, and I decided to plug the HDD into her dell and see what happens. I do, its recognized, but still no files. I run some windows disc utility and let it scan for errors and fix them, and when it was done I still had a empty HDD. I give up for a about a week. 

This morning I plug it back into my desktop, fire up nautilus as root, and bam...I have 2 files listed. FOUND.000 and $RECYCLE.BIN. Found contains all of the files I lost, but in FILE000x.CHK format. I find if I rename all of the files and move them to a new folder I create, they are back to normal. I assume the FOUND.000 folder is something the windows disk utility created, but either way this sucks. I have like 1000 files I have to manually rename, and no explanation as to why they disappeared in the first place.  

I know this was wordy, so thank you to anyone who reads the entire thing. If anyone has advice as to how to prevent these problems, I'm sure it would be appreciated by users in the future.

---

