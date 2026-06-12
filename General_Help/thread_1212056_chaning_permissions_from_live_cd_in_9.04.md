---
title: "chaning permissions from live cd in 9.04"
date: 2009-07-13
forum: General Help
---

### Post by mike1212 on 2009-07-13
Hello, any help would be greatly appreciated.  A couple weeks ago I upgraded to 9.04.  Things were fine at first but after a week I had to change about a thousand things using fsck when I booted up.  Then I was good for another week.  Now I can't boot into ubuntu (it goes to a grub prompt).  I've been reading forums and got some direction.  I'm thinking the best way to go is boot from a live cd, copy the data I want to save, then do a fresh install of 9.04.  Does that sound about right?

If so, I am then running into a problem with permissions.  I can read about half my data (picture/movies/music), but the other have I do not have permission to copy.  So even though I can see it, I can't move it off my system.  I've read a bunch about permissions but can't seem to change them.  Is this maybe a problem from a live cd?

side note:  I'm pretty bummed this happened after an upgrade.  I read something about a tracker bug?  Wonder if that's why I had trouble.  Anyway, my windows using friends are getting their diggs in now.

Thanks for any help,
Mike

---

### Post by oldos2er on 2009-07-13
Have you considered the possibility that your hard disk may be failing? Your mention of fsck concerns me.

 When you're running the LiveCD, run **gksu nautilus** to give yourself admin privileges, that should solve the file copy problem.

---

### Post by dave_i on 2009-07-13
Yes, I would worried that your hard disk is failing - if you ever think your hard disk is failing, you need to backup important data **immediately**, and get a new disk asap. You can test your disk by running badblocks from the livecd:

[http://ubuntumagnet.com/2008/01/checking-disks-errors-using-badblocks-command](http://ubuntumagnet.com/2008/01/checking-disks-errors-using-badblocks-command)

---

### Post by mike1212 on 2009-07-13
Thanks, I guess the hard disk failing could be a possibility.  Any way to test for that?

I read a few posts by people having similar problems as mine after updating to 9.04 so I was assuming the upgrade had more to do with than the hard drive.  

I'll try gksu nautilus to solve my copying files problem.

Does that seem like a reasonable way to go?  Copy my data then do a fresh install?

Thanks again,
Mike

---

### Post by bodhi.zazen on 2009-07-13
> **mike1212 said:**
> Does that seem like a reasonable way to go?  Copy my data then do a fresh install?

Thanks again,
Mike

Yes that will be fine, just back up your data to an external source (external CD / DVD / flash drive).

---

