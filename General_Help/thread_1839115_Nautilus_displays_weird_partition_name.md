---
title: "Nautilus displays weird partition name"
date: 2011-09-05
forum: General Help
---

### Post by mtanner on 2011-09-05
Apologies in advance if this is not the place to ask this.

I'm running Ubuntu 10.04 Lucid, 64-bit

I searched and found a thread which sounded similar to this one at: [http://ubuntuforums.org/showthread.php?t=1347448]("http://ubuntuforums.org/showthread.php?t=1347448") and tried remounting the partition in question but got "e2label: Bad magic number in super-block while trying to open /dev/sda8
Couldn't find valid filesystem superblock." as my response.  Maybe that's got something to do with the weird labeling in Nautilus?  See below:

So the story is: Nautilus has always displayed something like "150 GB File System" for a Win7 installation partition I have on the same disk with Ubuntu.  I also have on this disk a shared partition (Fat32) where I keep music and documents that I want to access from both Ubuntu and Win7.  It's 30 GB.  A while back, like a few months ago, the label on the desktop for this 30 GB fat32/msdos partition changed to something quite strange: "</dict> </p".  That's what it's labeled as on the desktop and inside the nautilus file manager.  It used to be "30 GB File System", similar to what the Win7 partition is labeled.

Stranger still, I have avant-window-navigator installed, and when I click on the "File Browser Launcher" dock applet, and it gives me a list of places to open, both the 150 GB Win7 partition (mounted as /media/WIN7) and the 30 GB shared partition (mounted as /media/SHARE) appear as "150 GB File System".  ...Until I mouse over one of the other "places" in that same menu, and then mouse back over the link for /media/SHARE ... and that's when the text for the link to /media/SHARE changes to whatever other entry I just moused over in the File Browser Launcher applet.  For example, I click the File Browser Launcher applet icon, mouse over "Videos", and then back over that 2nd "150 GB File System" link, and the text on it changes to "Videos".  It still opens /media/SHARE in Nautilus when clicked.  Just neither Nautilus, nor AWN know what the heck to call it.  I'm clueless.

Everything seems to work fine other than that, and it's not really a problem per se, but I can't help but wonder in the back of my mind if I screwed something up at some point :P.

---

