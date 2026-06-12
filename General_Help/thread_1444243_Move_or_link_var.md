---
title: "Move or link /var?"
date: 2010-04-01
forum: General Help
---

### Post by Twizzle on 2010-04-01
I have installed Ubuntu server 9.10 on a home server system with an 8Gb / partition and a 600Gb LVM /home partition.

Having now installed a number of things including Zoneminder and Wordpress, I have realised that maybe I should have put /var on an LVM partition as when I tried to log into the server today Ifound that / was at 98% and the webserver kept crashing!

I discovered that the main culprit was Zoneminder saving events and filling the space so I have created a symbolic link to a folder in my /home partition and son far (fingers crossed) it seems to work.

This has got me thinking though and I guess that the more I use programs like Wordpress and put some videos and photos on it, I am going to run into the same problem again, as the mysql database is stored on /var (as I understand it).

My thoughts now are either to;

a) reinstall and set up /var on the LVM partition, or 
b) move /var now, or
c) create a symbolic link to /var.

I have seen a number of posts about moving or linking but was just wondering what is considered the best / safest for long term usage. I would hate to do one then find out in six months or so when I have alot of saved data that I should have done the other!

At the moment the server install is only a week old so it would not be too much of an issue to reinstall, although I would prefer not to have to.

Thanks

---

### Post by john newbuntu on 2010-04-01
Yeah, /var becomes a monster once you install more software, especially with mysql and dpkg growing.  Option a looks good.  It is better off moving it into a separate filesystem(preferably on a different disk if you can afford one).  Experts can chip in here as it will help me too.

---

### Post by gmargo on 2010-04-01
I'd recommend leaving /var where it is, and just moving the piggies and create symbolic links.

For instance, my /var/lib/mysql (and -cluster) actually live in /home/database_storage/mysql (and -cluster).  Also my /var/lib/postgresql/8.3/main is actually in /home/database_storage/postgresql/8.3/main.

---

### Post by Twizzle on 2010-04-03
Well after trying to create a few symbolic links and messing the whole thing up, I reverted to option and and did a fresh install.

Like I said, it is a relativley newly installed server so I did not loose anything I have not got saved else where.

The lesson is, plan in advance and remember /var can grow and grow....:p

---

### Post by warfacegod on 2010-04-03
Had you considered resizing the OS partition?

---

### Post by dcstar on 2010-04-03
> **Twizzle said:**
> Well after trying to create a few symbolic links and messing the whole thing up, I reverted to option and and did a fresh install.

Like I said, it is a relativley newly installed server so I did not loose anything I have not got saved else where.

The lesson is, plan in advance and remember /var can grow and grow....:p

/var contains the Cache and Log folders, **if you do not maintain your system correctly** then these can easily fill up.

A properly maintained system should not have issues with /var if a reasonable amount of space is allocated initially.

---

