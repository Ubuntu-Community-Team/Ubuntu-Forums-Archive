---
title: "Wubi issue, probably because of RAID"
date: 2012-04-02
forum: General Help
---

### Post by kwski43 on 2012-04-02
I'm having problem installing any Ubuntu release using Wubi. It always comes with error: [http://i.imgur.com/jjFtn.jpg](http://i.imgur.com/jjFtn.jpg)
I'm not sure but I'm using hardware RAID - could it be the issue?

---

### Post by RJARRRPCGP on 2012-04-02
Looks like wrong type of installation. It's looking for the CD or DVD. Appears to be in live mode.

---

### Post by bcbc on 2012-04-03
What type of raid do you have?

---

### Post by kwski43 on 2012-04-03
It's Raid 5 on ICH8R, ICH9R, ICH10R family RAID Controller.

It's impossible that it's looking for the CD, I've installed same ubuntu in the exact way on my netbook and it actually worked without any problems.

---

### Post by RJARRRPCGP on 2012-04-03
> **kwski43 said:**
> It's Raid 5 on ICH8R, ICH9R, ICH10R family RAID Controller.

It's impossible that it's looking for the CD, I've installed same ubuntu in the exact way on my netbook and it actually worked without any problems.

It looks like it's trying to boot live-style or frugal-style (like Puppy) and can't find a CD or DVD image.

(And Puppy's been known to fail with an error kind of like that, because most distros don't like the Marvell PATA controller on my Asus P5QL Pro board.) 
(Which my optical drive is connected to.) 

**/dev/sr0** is the optical drive! O_O

---

### Post by bcbc on 2012-04-03
> **kwski43 said:**
> It's Raid 5 on ICH8R, ICH9R, ICH10R family RAID Controller.

It's impossible that it's looking for the CD, I've installed same ubuntu in the exact way on my netbook and it actually worked without any problems.

I haven't heard of problems with raid 5 (but I don't know a lot about raids either. But I know e.g. 1+0 is a problem though.)

Can you boot a live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")? That will give us a better idea about how Ubuntu is seeing your drive.

Also, if you want to, hit Esc... when it gives the countdown. Then from a grub prompt (hit 'C' to get there), enter:
```
ls
```
That will list your drives and partitions. e.g. drive: (hd0), partition: (hd0,1) etc. Maybe it will look like (hd0,msdos1), or ('dev/sda',msdos1) depending on the grub version.

Then you can look for the ISO:
```
ls (hd0,1)/ubuntu/install/installation.iso
```

I know it will be there, but it might indicate how grub sees the drive and add to the diagnostics from the bootinfoscript.

PS since you have a raid, maybe you'll see something different that (hd0,1).
PPS press Esc key to return from the grub prompt back to the grub menu.

---

