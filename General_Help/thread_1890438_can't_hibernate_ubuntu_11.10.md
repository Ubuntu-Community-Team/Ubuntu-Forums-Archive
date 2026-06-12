---
title: "can't hibernate ubuntu 11.10"
date: 2011-12-03
forum: General Help
---

### Post by LifeEnemy on 2011-12-03
Hi,

I have an Acer Aspire One 722. Now that I finally got around to putting ubuntu on it (glad to be away from windows again!) I can't seem to get the hibernate/suspend function to work. I found this guide: 

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/) 

but it's old. I downloaded uswsusp and managed to get s2ram to work, but when I use s2disk it freezes soon after waking up. How can I make this work, and how can I set these to be default actions in 11.10? Or, is there another way to fix suspend/hibernate?

thanks guys!

EDIT: new problem, similar. Marked unsolved.

---

### Post by manojankk on 2011-12-03
I heard same issue from my brother. Seems like a bug ? Anybody logged it ?

---

### Post by BC59 on 2011-12-03
> **LifeEnemy said:**
> Or, is there another way to fix suspend/hibernate?

To hibernate is needed a big swap. So if you have installed 2GB RAM you need 4GB of swap.

---

### Post by LifeEnemy on 2011-12-03
> **BC59 said:**
> To hibernate is needed a big swap. So if you have installed 2GB RAM you need 4GB of swap.

I have 3gb swap, 2 gb RAM. Could that be the cause of the problem? I want to make sure before I redo the partitions.

---

### Post by dFlyer on 2011-12-03
Increase your swap to 4 gig and see if that helps.

---

### Post by LifeEnemy on 2011-12-04
> **dFlyer said:**
> Increase your swap to 4 gig and see if that helps.

Since I haven't done anything on this computer yet I went ahead and reinstalled from the CD, resizing the partitions a bit. It seems to have worked for now. Thanks guys!

I'm enjoying some of the new features they've added since 10.04 :)

---

### Post by LifeEnemy on 2012-01-12
Hi guys,

The swap fix worked for a while, but now I have a strange new problem. Suspend works fine, but hibernate gives me trouble. THe last few times I've used it I've come to find my computer dead the next day. I'm not sure if it's turning itself on or just draining the battery, but even after I plug it in and boot up the computer will freeze after hibernation (even if it doesn't get a chance to drain the battery). It freezes on the lock screen usually, but last time it didn't freeze until a few minutes after I unlocked it. Any ideas?

Thanks!

---

