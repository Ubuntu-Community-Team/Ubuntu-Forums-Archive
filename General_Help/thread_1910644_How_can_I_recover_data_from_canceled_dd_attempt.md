---
title: "How can I recover data from canceled dd attempt"
date: 2012-01-17
forum: General Help
---

### Post by tonyism7 on 2012-01-17
I wanted to clone a hard drive using dd, but when I typed the command I absentmindedly put in the wrong destination hard drive. I realized my mistake about ten seconds into the process and canceled it. I feel like a real idiot now.

I had about 1.5 terabytes of data on the drive I accidentally wrote to and would like to try to get as much as that data back as possible. After running through fsck I can only access a lost + found folder that I believe came from drive I was attempting to clone.  Looking in gparted, the drive still shows as having 1.5 terabytes on it.

Any suggestions on what would be the best way to access some of the old files I had? Thanks

---

### Post by imachavel on 2012-01-17
best advice, completely repartition destination hard drive, and then once there, reinstall and put files on. But then I'm sure you thought of that

so, question #1, original hard drive, or external I'm not sure, the files on it, are they gone now? 

question #2, destination drive, do you have a second computer? Can you pull that hard drive out, connect it to second computer, remove files, then reformat partition table and OS on first hard drive, then put files back on second time? I know very little about dd:

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

I must admit, if I was going to clone a drive/capture an image/whatever, I would probably not do it unless I was in a server environment, and had done it before. Now for those who just don't want to back up their files and do a fresh install, it's not the biggest deal in the world. But I know nothing about dd, however there are lots of great threads on here about the same problem, one I just viewed a few minutes ago. Have you looked through all those? Sorry but also in your partition table if a lot of space is taken up on a partition, then obviously the files are there. However you can get those files back, do it. Give it your best shot. Sorry I don't know more but can't you see that these beans aren't roasted? Haha

---

### Post by blackbird34 on 2012-01-17
Found this in my bookmarks. It should help, i think:[URL="http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/"]

http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/[/URL]

And as this is an external hard drive you're doing  this on, I don't think you'll need to be on live CD. 

Good luck:popcorn:

---

### Post by tonyism7 on 2012-01-17
@ imachavel: I still have all the files on the original hard drive, so I'm not worried about that. They're both internal hard drives so I'll try pulling it out and seeing what I can do on another computer. And yeah next time I want to do this I'm using clonezilla or something similar, I don't wanna go through this again even if it was all user error.

@blackbird34: Thanks for the link, that looks pretty good, I'll try that tonight as soon as I get home.

---

### Post by dragonfly41 on 2012-01-17
Be aware that with some free recovery utilities you may not (easily) recover file names.   This can be a problem with such large drives.

If you have Windows computer at hand ..

you can try running these recovery utilities (before having to buy as a last resort) on your removed hard drive (plugged into Windows as external drive) to explore just what files you *might* be able to recover  ..

[http://www.stellarlinuxdatarecovery.com/buy-linux-recovery-software.php](http://www.stellarlinuxdatarecovery.com/buy-linux-recovery-software.php)

and

[http://www.recovermyfiles.com](http://www.recovermyfiles.com)

---

