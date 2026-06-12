---
title: "How do I update Ubuntu 9 after memory increase (512mb-1Gb ram)?"
date: 2009-07-19
forum: General Help
---

### Post by Nazaroo on 2009-07-19
What can I do after installing new RAM to improve performance of Ubuntu?

I installed it when I had 512 mB and now have 1 Gb.

Can I decrease disk swapping, or change some config files?

thanks
Nazaroo

---

### Post by merlinus on 2009-07-19
Ubuntu should automatically recognize the additional ram.  And unless you need the hdd space, why not leave /swap alone?

---

### Post by Nazaroo on 2009-07-19
well one reason is that I am actually having HDrive problems...I have a 10 Gig boot drive and it seems to be almost full, whereas it should have about 4 Gig still empty. I am trying to trace down where the HD space has gone.

Is there a 'cleanup' program that deletes redundant or unneeded source files?

thnks
Nazaroo

---

### Post by merlinus on 2009-07-19
Here is good how-to created by a forum member:

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Also look at System/Administration/Computer Janitor if you are running 9.04.

---

### Post by t0p on 2009-07-19
> **Nazaroo said:**
> 
Is there a 'cleanup' program that deletes redundant or unneeded source files?


'Source files'?  Do you mean 'package files'?  If so, there's **apt-get clean** and **apt-get autoclean**.  Check out

```
man apt-get
```

for details.

---

### Post by -=hazard=- on 2009-07-19
sudo apt-get autoremove

sudo rm -v /var/cache/apt/archives/*.deb

sudo rm -v /var/log/*.gz

---

