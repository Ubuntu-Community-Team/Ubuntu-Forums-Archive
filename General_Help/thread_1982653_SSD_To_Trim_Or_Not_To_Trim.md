---
title: "SSD: To Trim Or Not To Trim?"
date: 2012-05-18
forum: General Help
---

### Post by jim_deadlock on 2012-05-18
I've had a SSD (OCZ AGILITY 3 SATA III 2.5" 120G) for a couple of months now. I have my root partition on it and using a separate HDD for /home and I must say it all runs like greased lightning, I'd highly recommend it.

Anyway, up until now I've been blissfully unaware of Trim but I've just been googling various forum posts and now I'm wondering if it's a good idea to enable trim to minimise wear and tear on my SSD. Does anyone have any advice on whether it's recommended or not?

---

### Post by idoitprone on 2012-05-18
> **jim_deadlock said:**
> I've had a SSD (OCZ AGILITY 3 SATA III 2.5" 120G) for a couple of months now. I have my root partition on it and using a separate HDD for /home and I must say it all runs like greased lightning, I'd highly recommend it.

Anyway, up until now I've been blissfully unaware of Trim but I've just been googling various forum posts and now I'm wondering if it's a good idea to enable trim to minimise wear and tear on my SSD. Does anyone have any advice on whether it's recommended or not?

yep it is a good idea
writes are bad on a ssd
trim is just a feature on ssd just like smart on a hdd
[http://en.wikipedia.org/wiki/TRIM](http://en.wikipedia.org/wiki/TRIM)
what you want is discard and noatime
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by oldfred on 2012-05-18
I did not add discard to my fstab right away, but have now. I did find the site below where the poster is against trim but wants a cron task every night. I ran that just after setting discard and it showed it did something.

HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)

Not required with newer kernels
[http://disktrim.sourceforge.net/](http://disktrim.sourceforge.net/)
Typical fstab entry:
UUID=d65e4ad3-6315-4838-97a1-ec574cb8575f / ext4 noatime,discard,errors=remount-ro   0       1

[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq]

---

### Post by jim_deadlock on 2012-05-19
Checking if TRIM is working I get exactly the same result both with and without the tempfile. Note the first 4 lines are not zeros, so I'm not sure whether this meets the requirement of "If TRIM is properly working the result of the last command should be a bunch of zeros"...?

EDIT: well I've updated my fstab so I guess I'm all set, thanks guys.

```
# hdparm --read-sector 4096 /dev/sda

/dev/sda:
reading sector 4096: succeeded
8100 0000 8100 0001 8100 0002 8100 0003
8100 0004 8100 000c 8100 000d 8100 0018
8100 0028 8100 003e 8100 0079 8100 00ab
8100 0138 8100 016c 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 0000
```

---

### Post by dcstar on 2012-05-20
> **jim_deadlock said:**
> 
.........
Anyway, up until now I've been blissfully unaware of Trim but I've just been googling various forum posts and now I'm wondering if it's a good idea to enable trim to minimise wear and tear on my SSD.

TRIM has absolutely nothing to do with "minimise wear and tear on my SSD", it is solely to keep the SSD's write performance at maximum.

Without having TRIM used on **every** partition on the SDD eventually any writes will eventually exhaust the pool of unused blocks and force the SSD to basically take 3 times longer to re-write blocks (Copy, Erase then Write versus Write).

TRIM lets the SSD erase blocks in the background once it is informed that they are no longer used.

---

### Post by chocklet on 2012-05-20
Yep you absolutely want discard & noatime.

Over a year ago, I got one of the smallest & slowest SSDs obtainable.  And it is still snappy.  That is, it boots noticably faster than any other PC in the house and loads applications quickly.  My fstab is similar to oldfred's "typical" example.

I've tried to reduce writes to the SSD ("wear and tear") by putting /var on a spinning data drive, and by mounting /tmp in RAM.

---

### Post by risotto77 on 2012-05-20
I am wondering what to do with the information in this thread. I have a ssd and feel no issue with performance so far. Ubuntu 12.04 takes 12 seconds to load from power on as an example (edit 2: but guess the conserns in this thread is about writing perfromance and durability of writing performance). I do not like to mess with system if I do not have to but of course I'd like to get the best out of my hardware. 

I really think Ubuntu should take care of matters like this. Have anyone adressed this issue for the developers?

Edit: I added noatime and discard to options for my ssd in fstab as well. Hope that is good.

---

### Post by habana on 2012-05-20
> I really think Ubuntu should take care of matters like this. Have anyone adressed this issue for the developers?

Everybody's system is different so it's a bit hard for the developers. For example I have a mixed SSD/HDD system so I can't enable noop or deadline in grub - I used the sysfsutils utility.

I agree with all that discard and noop (or deadline) are essential but I believe that the current crop of SSDs are much more robust than they used to be in terms of write cyles and the lengths that some peple go to to reduce them are no longer appropriate. Personally I have enabled noatime and moved the tmp directory to ramdisk but that's it.

---

