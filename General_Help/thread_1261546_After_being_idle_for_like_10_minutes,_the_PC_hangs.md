---
title: "After being idle for like 10 minutes, the PC hangs"
date: 2009-09-08
forum: General Help
---

### Post by davidcmc on 2009-09-08
Hello.
Firstly, my system:

Ubuntu 9.04 x86_64 installed in an external USB HD
C2D E8500 @ stock
Gigabyte EP43-DS3L
2x2Gb Kingston 800
HD4850 (Catalyst 9.8 x86_64 installed following AMD tutorial in pdf file)
Compiz: Activated

I've disabled screensaver and all other power management options already.
When I leave my computer idle for something like 10 minutes, it hangs and nothing works. I can move the mouse, but nothing works.
Just googled it and found out that some people have the same problem, but can't seem to find a real fix for that problem.

Can anyone help me?

Thanks.

--David

---

### Post by P4man on 2009-09-09
Is it possible those 10 minutes is what it takes for the USB drive to spin down, and its not spinning up again?

---

### Post by wojox on 2009-09-09
Try going to System > Preferences > Appearance > Visual Effects  = None.

See if that does anything.

---

### Post by rob-ward on 2009-09-09
What make it the drive? Is it a maxtor or a seagate?

As suggested it could be that the drive is spinning down and not spinning back up. 

If it is a seagate or certain types of maxtors then the command ```
sudo hdparm -Z /dev/yourdrive
```
may fix the problem, if not then to confirm if it is the drive spinning down at certain times then you can just create a script that pings the drive every minute or so to see if it keeps it alive

---

### Post by davidcmc on 2009-09-09
> **P4man said:**
> Is it possible those 10 minutes is what it takes for the USB drive to spin down, and its not spinning up again?

Maybe? How do I see that?

> **wojox said:**
> Try going to System > Preferences > Appearance > Visual Effects  = None.

See if that does anything.

Going to try that.
Thanks.

> **rob-ward said:**
> What make it the drive? Is it a maxtor or a seagate?

As suggested it could be that the drive is spinning down and not spinning back up. 

If it is a seagate or certain types of maxtors then the command ```
sudo hdparm -Z /dev/yourdrive
```may fix the problem, if not then to confirm if it is the drive spinning down at certain times then you can just create a script that pings the drive every minute or so to see if it keeps it alive

It's a Samsung S2 Portable 320Gb ([http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=87&subtype=88&model_cd=429&ppmi=1177](http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=87&subtype=88&model_cd=429&ppmi=1177))
Going to try that command.

Thank you all.

--David

---

