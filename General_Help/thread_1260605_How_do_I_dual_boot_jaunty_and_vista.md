---
title: "How do I dual boot jaunty and vista?"
date: 2009-09-07
forum: General Help
---

### Post by Dustin2128 on 2009-09-07
for some reason, the excellent disc partitioner in 8.04 has been removed and replaced with a.... less intuitive one. It says the only options are completely wiping vista (love to but not my comp) or 'manually' partitioning the discs which appears to do close to the same thing. Is there any way to access the older (circa 8.04) 'slider' partitioner? Also, good work on wi-fi support, using this on the live cd.

---

### Post by glenuk on 2009-09-07
when i installed my copy of ubuntu 9.04 there was an option to install side by side
& when i had to install it again to recover data i chose the manualy size the partition & i had the slider to resize the partition manualy

---

### Post by Dustin2128 on 2009-09-07
I'll post some screen shots to clarify

---

### Post by Dustin2128 on 2009-09-07
come on, anybody? it takes 15-25 mins to install after settings, I don't have all the time in the world

---

### Post by glenuk on 2009-09-07
have you tried installing it more than once?

---

### Post by Dustin2128 on 2009-09-07
do you mean restarting the partition manager? yes, many times. I tried booting back into vista to shrink the partition from there, but despite having over 48 GB of free space, it won't allow me (hate that phrase) to create more than 800 *megabytes* of free (unpartitioned) space!!!

---

### Post by glenuk on 2009-09-07
so i'm guessing you've tried starting the install from the start.
have you tried a third party partition manager in windows?

---

### Post by Dustin2128 on 2009-09-07
> **glenuk said:**
> so i'm guessing you've tried starting the install from the start.
have you tried a third party partition manager in windows?

no, I don't use windows on a regular basis. what's a good third party partition manager?

---

### Post by glenuk on 2009-09-07
i used to use partition magic when i used windows but you had to pay for it but thinking about it i think it has a trial version i found it quite easy to use

---

### Post by Dustin2128 on 2009-09-07
ha, me, pay for software

---

### Post by Sgt-Slyde on 2009-09-07
I'm a big fan of Hiren's Boot CD - it has a lot of disk partition tools (along with lots of other tools as well).  If you're pressed for time, though, just see if you can download a partitioning tool from Hiren's website rather than download and burn the entire CD ISO image.  It's a bootable CD, runs on a Linux kernel (even though the CLI seems to be modeled after DOS) and can be really useful but, as I wrote, that takes time.  I used it to repartition my wife's Vista laptop and opened up several gig (don't remember how many) to install Xubuntu and it worked okay.

---

### Post by fluffman86 on 2009-09-07
The "manual partition" option in the Ubuntu installer is just a front end for parted.  You should be able to click a partition, then edit, then resize it.  

Of course, if that doesn't work, then from the live CD go to System > Administration > Parition Editor to open gparted.

I have actually had some trouble with Gparted running in the Ubuntu live CD in the distant past, so if you run into any trouble, you can get a bootable gparted live cd as well.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by fluffman86 on 2009-09-07
The "manual partition" option in the Ubuntu installer is just a front end for parted.  You should be able to click a partition, then edit, then resize it.  

Of course, if that doesn't work, then from the live CD go to System > Administration > Parition Editor to open gparted.

I have actually had some trouble with Gparted running in the Ubuntu live CD in the distant past, so if you run into any trouble, you can get a bootable gparted live cd as well.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by glenuk on 2009-09-07
like i said i think theres a tiral version but theres also the option of piracy but have a search round for a free one that you are comfortable with

---

### Post by raymondh on 2009-09-07
> **Dustin2128 said:**
> do you mean restarting the partition manager? yes, many times. I tried booting back into vista to shrink the partition from there, but despite having over 48 GB of free space, it won't allow me (hate that phrase) to create more than 800 *megabytes* of free (unpartitioned) space!!!

You may have run into those immovable files (paging, etc) that are spread out by windows throughout its' partition.

Here's a link on a workaround:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Defrag as well.

Good luck.

---

