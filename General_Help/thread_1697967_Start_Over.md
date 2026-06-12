---
title: "Start Over"
date: 2011-03-01
forum: General Help
---

### Post by richwein on 2011-03-01
Starting fresh.

I've been using Ubuntu for quite a while, several years, though several upgrades.  Experimented with various things, uninstalled some and various other messy activities.  Some things don't work as well as they used to.  Sometimes my system crashes, or hangs for a while before coming back.  I still get a KDE screen when I shut down, though I attempted to uninstal that desktop.    

I would like to start over, that is with as little trouble possible to reinstall from scratch.  Have to save my user directories, also the directories for my LAMP applications.

Anything I'm forgetting ?

What is the best approach ?

---

### Post by Hedgehog1 on 2011-03-01
Not knowing your current partition configuration, you may already be doing this:

Separate your OS partition (/dev/sda1 --> '/') from your home (and data) partition (/dev/sda2 --> '/home') when you install from scratch.

Will you be backing up to and external hard drive? Or CD/DVDs?

---

### Post by dabl on 2011-03-01
High level -- 

(a) back up everything you care about
(b) use GParted from a Live CD and make any adjustments to your hard drive partitions that you need to make, and reformat the one you need for the OS
(c) download and burn the Alternate installation CD (it has more packages and skips the live desktop thing
(d) boot the CD and follow the steps to install on your selected partition


However, timing being what it is, do you really want to install 10.10 just weeks before 11.04 is released?  Just a thought.

---

### Post by richwein on 2011-03-01
Great suggestions,

dabl, 11.04 is a thought, I might as well use up a weekend and get something brand new.  Thanks.
hedgehog1, backing up to DVD, thanks

---

### Post by Hedgehog1 on 2011-03-01
> **dabl said:**
> 
However, timing being what it is, do you really want to install 10.10 just weeks before 11.04 is released?  Just a thought.

I suppose that it depends on how adventurous the OP is.

Somehow I sense a conservative nature here...  It is a gift we Hedgehogs have...  Sometimes...

:KS

Edit: And ***The Hedge*** guesses wrong!

---

### Post by dabl on 2011-03-01
@richwein, the hog makes a good point here:

> **Hedgehog1 said:**
> I suppose that it depends on how adventurous the OP is.



If life and limb and your income depend on 100% solid stable performance, with flawless desktop environment, you might want to hold off installing 11.04 until it is released.  It looks good here (Kubuntu) on my VM, but I wouldn't bet next week's paycheck on having it working totally reliably every day between now and release date in April.

On the other hand, there's no charge to download the Daily Build CD, and check it out ....  :lolflag:

---

### Post by Hedgehog1 on 2011-03-01
> **dabl said:**
> @richwein, the hog makes a good point here:


That's ***The Hedge***, if you please... :D

The OP can also postpone the install until 11.04 is ready; but honestly, I would still suggest no higher then 10.10 for about a month after 11.04 ships.

That lets the 'uber geeks' find the little things that need finding first.

***The Hedge***  

:KS

---

### Post by nm_geo on 2011-03-01
> **Hedgehog1 said:**
> That's ***The Hedge***, if you please... :D

The OP can also postpone the install until 11.04 is ready; but honestly, I would still suggest no higher then 10.10 for about a month after 11.04 ships.

That lets the 'uber geeks' find the little things that need finding first.

***The Hedge***  

:KS

Hmmm... uber geeks   :lolflag:   nm_geo is one..

Now to the OP I believe everyone is giving you good advice.  Natty is becoming more stable daily, but it is not ready for consumption by the general public. Now if you enjoy fixing broken things weelky and want to be an Uber Geek it is right up your alley: or if you want to run Natty on another partition that might fit.

You kill me Hedge

---

### Post by richwein on 2011-03-02
Thanks for the tips and suggestions, decided to reinstall 10.10.

---

