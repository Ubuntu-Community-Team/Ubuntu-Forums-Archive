---
title: "help shrink 6.5gb remastersys dist"
date: 2011-11-27
forum: General Help
---

### Post by elliotn on 2011-11-27
help m,e shrink remastersys to less than 3gb please, I have trie,d for 2 weeks but it keeps gettin over 6.5gb, I have cleaned the system, uninstalled most programs, removed files in home but still can't get below 6gb...any help

---

### Post by elliotn on 2011-11-27
ideas

---

### Post by deserthowler on 2011-11-27
Just a thought.  Before you start doing a new remastersys, did you clean the cache?  Not sure if this is a problem or not but might be worth checking.

I also do my remastersys after a reboot to make sure all of the junk is clear.

Earl

---

### Post by oldtimer7777 on 2011-11-27
> **elliotn said:**
> help m,e shrink remastersys to less than 3gb please, I have trie,d for 2 weeks but it keeps gettin over 6.5gb, I have cleaned the system, uninstalled most programs, removed files in home but still can't get below 6gb...any help

How much software did you add to your system? 

Have you used remastersys on your system recently, successfully? 

Have you cleaned out all your cache's with bleachbit?

sudo apt-get install bleachbit
sudo bleachbit

I use Remastersys for my backups religiously.  I move all my Home folder files to an external hard drive first before running Remastersys.

Relinux works great too:

[https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/](https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/)

---

### Post by elliotn on 2011-11-27
> **oldtimer7777 said:**
> How much software did you add to your system? 

Have you used remastersys on your system recently, successfully? 

Have you cleaned out all your cache's with bleachbit?

sudo apt-get install bleachbit
sudo bleachbit

lot of software's yes but have removed 95% of them even gwibber, libre impress etc, I will use bleachbit and see, 2weeks ago I did one and it was 1.6gb

---

### Post by oldtimer7777 on 2011-11-27
> **elliotn said:**
> lot of software's yes but have removed 95% of them even gwibber, libre impress etc, I will use bleachbit and see, 2weeks ago I did one and it was 1.6gb

I install quite a bit of software myself before running Remastersys. I think everyone should have a backup of their dist on hand at all times.. It is usually around 2.2 Gb, but I recommend if you are going to install that much software, to use Remastersys on a freshly installed system with everything you want on it first. Over time, sometimes bleachbit can clean out cache files that take up space..  Make sure to clean out your Remastersys temp folder as well. Check with deborphan for any stray files that shouldn't be there too. Use Ubuntu Tweak to clean out any other Caches, and Package configurations. And here is here is how you can get gtkorphan working on your system to clean out stray packages:

sudo apt-get install gtkorphan
sudo gtkorphan

---

