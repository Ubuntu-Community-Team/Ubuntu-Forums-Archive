---
title: "new machine...can't access old harddrive"
date: 2006-02-15
forum: General Help
---

### Post by harty83 on 2006-02-15
Hello,

I bought a new machine b/c my old one was on the fritz.  I would like to add the old harddrive to my new machine so that I can access all my files.  However, when I have both hda's connected, BIOS will not recongize either of them.  It will recognize one at a time (boot up from each one), but not when both are connected.  Is this maybe because grub is installed on both drives?  If so, how would I get rid of grub from the old hd?  If not, what are possible issues and how would I go about fixing it?

To summarize, I have two harddrives both with ubuntu and grub installed on it.  I want to be able to boot from my new one but access the old one.  BIOS does not like both hooked up at one time.  How do I fix this?

Thanks!
Alan

---

### Post by sbassett on 2006-02-15
To rule your fist concern out, grub will not affect the bios recognition. Have you checked the HD jumper settings? Make sure your main drive is set to master, and the old drive you wish to retrieve your files off of is set to slave. After this is done, and the bios recogizes both (which it should, unless the old hard drive is beyond fried) boot up normally. Then open a terminal and enter the following:

sudo mkdir /mnt/olddrive
sudo mount -t <filesystemtype> /dev/hdb1 /mnt/olddrive

where filesystemtype would be how the drive is formated.
ext3 for ubuntu (in most cases, unless a special install was done)
vfat for win9x, etc even some wnxp
ntfs for majority of winxp or 2000

/dev/hdb1 should get you through if the old OS is on the first partition, any doubts, please use fdisk -l /dev/hdb.

After this has been completed, the entire contents of your drive should now reside within /mnt/olddrive.

This is for this boot only (as you stated you wanted to copy files, I am under the assumption that you will be removing this drive after this has been completed.).

Any questions, please post.

---

### Post by harty83 on 2006-02-15
Thanks.  I did not know about the hd jumper settings.  That was the problem.  

Ha, the old harddrive is not fried at all.  Just really old (the machine itself was going on the fritz).  And now, I fried my new one (well actually used one that came with the new/used machine, so its new to me)!!  AWAYS UNPLUG THE POWER BEFORE MESSING WITH THE HARDDRIVES.  Sometimes I amaze myself with my own stupidity.

Sigh.  Oh well, excuse to buy a new 120 gig.

---

