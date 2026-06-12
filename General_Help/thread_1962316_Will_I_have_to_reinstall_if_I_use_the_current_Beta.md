---
title: "Will I have to reinstall if I use the current Beta of Precise?"
date: 2012-04-20
forum: General Help
---

### Post by thatguymark on 2012-04-20
I've been helping a small non-profit and had planned to gradually change them over to Precise from Windows once it's released since it's a LTS, but as it happens it looks like they are having Windows malware issues now. I am making a trip on-site tomorrow, and I'd really like to avoid having to do it again in a week because the travel is a bit costly for me.

So since it's only a few days away, is it possible that I would be able to just update the current beta remotely?

---

### Post by thatguymark on 2012-04-20
Or maybe I should install 11.10 instead? Just wondering what makes the most sense.

---

### Post by 3rdalbum on 2012-04-21
The beta will become the release version. Just run the Update Manager on or after release day and click the Check button, and then install whatever updates are available.

---

### Post by thatguymark on 2012-04-21
Thanks!

---

### Post by Mark Phelps on 2012-04-21
IF it were ME, I would install 11.10.  why? 

Because (1) the Beta is pre-release, meaning it's NOT final, and it may still have problems that will affect your clients.  

And (2) I don't know if you can do the update remotely.  Not something I've tried.  If you can't, then your clients are going to be stuck with a Beta version of Ubuntu -- which is not good.

---

### Post by Paqman on 2012-04-21
You can do the upgrade remotely if you can connect to the machine over something like SSH. This is how servers are normally upgraded. The command is:
```
sudo do-release-upgrade
```

---

### Post by 3rdalbum on 2012-04-22
> **Mark Phelps said:**
> IF it were ME, I would install 11.10.  why? 

Because (1) the Beta is pre-release, meaning it's NOT final, and it may still have problems that will affect your clients.  

There may be at release, too. It's only four days away! There probably aren't too many new fixes coming down in the next few days, and you'd imagine most post-boot showstoppers have been found. I'm even running 12.04 from just after Beta 2 was released, with literally no issues :-)

> And (2) I don't know if you can do the update remotely.  Not something I've tried.  If you can't, then your clients are going to be stuck with a Beta version of Ubuntu -- which is not good.

You can update remotely. There's nothing especially wrong with using the beta for a long time - I mean, I'm using early Beta 2, and a friend was using 8.04 Beta 2 for months after release. In fact they're still using 8.10 even today... I should really make time to see my friend with a shiny new 12.04 disc :-)

---

