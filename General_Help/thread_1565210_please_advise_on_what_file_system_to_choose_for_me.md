---
title: "please advise on what file system to choose for media backup drive"
date: 2010-08-31
forum: General Help
---

### Post by Elvis99 on 2010-08-31
hey everybody,

I have a 500 GB external drive where I would like to keep my media files, mainly photos - I will use it only with ubuntu, so FAT32 and NTFS are out of the question - I don't trust them, especially not FAT32.

So, with these things in mind, I have the option of using ext2,3,4. From what I know, ext2 does not use journaling (journaling would make sense with large amounts of data, I guess?) but what's the difference between ext3 and ext4 (and maybe XFS?) - what are the advantages and disadvantages? I've read that ext3 does not need to be defragmented, but that's all that I know about these file systems, so could someone please translate all the differences and advantages of the file systems in a nutshell? 

Any help much appreciated* :)***

---

### Post by gzarkadas on 2010-08-31
Use what you have as default for running your system (that is either ext3 or etx4). Equally important to the medium though, is what and how you backup. Take the time to read this entire page (the recommendation above also stems from there): 

[[FONT=Verdana]Reliable Linux backups: How to backup Linux, BSD and other Unix-like systems properly[/FONT]]("http://www.halfgaar.net/backing-up-unix")

---

### Post by Spice Weasel on 2010-08-31
A lot of people think ext3 is much more reliable. It certainly has been in use longer, so I'd probably go with that. It's what I'm using on my external HD now.

---

### Post by xtnsgo on 2010-08-31
All my external USB hard drives are NTFS, mainly because one never knows when one might need to plug into a Windows box.  (My family, friends, and job all use Windows, so when i lug a drive from home, it's no sweat.) If it's used mainly for storage, NTFS is fine--i've gone several years without a problem, contrary to what some of the more devout had told me to expect.  Also, in my experience, extX isn't very tolerant of hotplugging--I've lost data by accidentally knocking the USB plug out.  

As far as extX re: defragging, my impression has been that it's simply unnecessary.  I've never defragged an extX drive and have yet to experience the sluggishness virtually guaranteed when a Windows drive isn't defragged regularly.  The urge to defrag was hard to fight after so many years of it being part of my routine!  

Through Karmic I had been using ext3 because I was getting all sorts of weird read errors with ext4, but since going with it on my Lucid install I've found none of the problems I used to have.  It's been reliable, and much faster in almost every way...

Anyway, that's my two-cents...  Good luck!

---

### Post by Elvis99 on 2010-09-01
hey,

thank you all for your opinions and your time to answer such a noobish question! I think I'll go with ext3 although I was not aware of the hotplugging issue, thanks xtnsgo for pointing this out - but I guess, I should be fine if I "eject" each drive before unplugging (while external HDDs are plugged in I always go for eject, but with USB Sticks I tend to pull them out as soon as I'm done with reading/writing them)

---

