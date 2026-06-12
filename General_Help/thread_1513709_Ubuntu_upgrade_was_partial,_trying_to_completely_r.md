---
title: "Ubuntu upgrade was partial, trying to completely remove ubuntu and reinstall"
date: 2010-06-19
forum: General Help
---

### Post by soadrocks79 on 2010-06-19
What exactly should i do. My ubuntu is currently so messed up that it won't download all its packages because there are too many errors when it tries. It only opens up into a command prompt. I have a live cd of 10.04 im just not sure how to uninstall the current version and install it from the live cd.

---

### Post by Tim Sharitt on 2010-06-19
If you want to start over with a clean install just run the installer normally and let the partitioner format the old partition for the new install. This will erase all the files on the current install, so be sure to backup anything you want to keep.

---

### Post by soadrocks79 on 2010-06-19
i realized this just after i said it but thank you anyway

---

### Post by linfidel on 2010-06-19
I wouldn't count on the partitioner to do the right thing - in my experience, it rarely does.  I've had it try to use some tiny bit of space that was not enough for the OS to even run very well.

Best thing is to us gparted on the live CD to delete the partitions first.

ps:
Hey, Tim... Hello from a former Alabama native.  I grew up in B'ham, but left long ago for California (in the 70s).

---

### Post by soadrocks79 on 2010-06-20
im slightly confused. im currently running the live disk so what should i do?

---

### Post by wilee-nilee on 2010-06-20
> **soadrocks79 said:**
> im slightly confused. im currently running the live disk so what should i do?

Linfidel's advice is bogus ignore it, it is personal experience due to inexperience. If your not dual booting just hit the install, and choose the install to the whole HD. I am assuming you have nothing you need to save here and are not trying to dual boot.

---

### Post by linfidel on 2010-06-20
> **wilee-nilee said:**
> Linfidel's advice is bogus ignore it, it is personal experience due to inexperience. If your not dual booting just hit the install, and choose the install to the whole HD. I am assuming you have nothing you need to save here and are not trying to dual boot.
Inexperience?  Well, maybe with reinstalling to the entire disk; I don't ever need to do that.  But I've had plenty of experience installing multiple systems on a disk, and I know the pros and cons of various methods.  

Some of us are experienced enough so we don't need to reformat the disk every time something goes wrong.  I guess you have a lot of experience reinstalling.

There, now, doesn't it feel good to get insulted by strangers?  Go ahead, keep it up if it makes you feel good.

BTW, deleting unused partitions first never hurts; in that way, I don't have to *make assumptions* about what else in on the disk. For someone who is inexperienced, it eliminates one more chance of having something go wrong.

---

### Post by wilee-nilee on 2010-06-20
> **linfidel said:**
> Inexperience?  Well, maybe with reinstalling to the entire disk; I don't ever need to do that.  But I've had plenty of experience installing multiple systems on a disk, and I know the pros and cons of various methods.  

Some of us are experienced enough so we don't need to reformat the disk every time something goes wrong.  I guess you have a lot of experience reinstalling.

There, now, doesn't it feel good to get insulted by strangers?  Go ahead, keep it up if it makes you feel good.

BTW, deleting unused partitions first never hurts; in that way, I don't have to *make assumptions* about what else in on the disk. For someone who is inexperienced, it eliminates one more chance of having something go wrong.

Don't take it personally the advice was based on this.
> I wouldn't count on the partitioner to do the right thing - in my experience, it rarely does.
frankly this makes no sense, under the described situation.

---

### Post by linfidel on 2010-06-21
> **wilee-nilee said:**
> Don't take it personally the advice was based on this.

frankly this makes no sense, under the described situation.
I don't know what the first sentence even means, but for the 2nd, all I can say is some of us know all too well how accurate new users describe the situation.

You made assumptions that were not stated - I didn't.  The OP never said what else was installed, or that he wanted to reformat the entire disk.

But hey, if it makes you feel good to think your way is always right, go ahead.  What do I know compared to you - you've been around here almost a year, I'm sure you know what you're doing.

---

