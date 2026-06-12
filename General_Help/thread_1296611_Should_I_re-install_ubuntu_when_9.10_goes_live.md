---
title: "Should I re-install ubuntu when 9.10 goes live?"
date: 2009-10-20
forum: General Help
---

### Post by white-zilla on 2009-10-20
Once 9.10 goes live, I know I can upgrade to the live version, but a few of my friends have been telling me that its better to just format and put the fresh new version on from scratch.

Is this the best way to do things? Is it REALLY that much better to format?  I dont feel like spending a day or two re-configuring everything

---

### Post by Roasted on 2009-10-20
I recommend it, yes. But I do things on separate partitions. I have root on one 20gb partition and the rest of my stuff mounted to my home partition.

That way I can reinstall Ubuntu without losing any of my personal settings or any of my personal data. All I have to do is reinstall the actual programs, but if you know what you need, it's easy enough to sudo apt-get this and that and this and that etc etc to get back on track. 

I recommend you format for that exact reason. Do a manual partition setup and add root to like 15-20gb (which is overkill but, I like overkill) and the remainder to home. That way in the future you can do a fresh install of Ubuntu and retain all of your personal stuff.

Just remember if you do this - do not check "format" for your home directory during the install process. :)

---

### Post by fluffman86 on 2009-10-20
I upgraded my laptop, even though I normally do a fresh install.  But I only did that because I just did a fresh install and manually set my HDD to use the new ext4.  

So, if you manually set Jaunty to use ext4, then just do a normal upgrade.

If you did an automatic jaunty install, then you should back everything up and format all of your partitions as ext4 in Karmic.

---

### Post by zzzBrett on 2009-10-20
> **Roasted said:**
> I recommend it, yes. But I do things on separate partitions. I have root on one 20gb partition and the rest of my stuff mounted to my home partition.

That way I can reinstall Ubuntu without losing any of my personal settings or any of my personal data. All I have to do is reinstall the actual programs, but if you know what you need, it's easy enough to sudo apt-get this and that and this and that etc etc to get back on track. 

I recommend you format for that exact reason. Do a manual partition setup and add root to like 15-20gb (which is overkill but, I like overkill) and the remainder to home. That way in the future you can do a fresh install of Ubuntu and retain all of your personal stuff.

Just remember if you do this - do not check "format" for your home directory during the install process. :)


I agree with this.  Keeping HOME on a separate partition really is crucial.

---

### Post by white-zilla on 2009-10-20
oooOOOooo, i think i'll do a fresh format and set up everything like that.  Thanks for the info

---

### Post by 3rdalbum on 2009-10-20
When Ubuntu 9.10 comes out, you shouldn't have any problems dist-upgrading to it. At the moment the development is moving so fast that the process might be a bit hair-raising.

---

