---
title: "Ubuntu Keeps Crashing... :("
date: 2011-03-13
forum: General Help
---

### Post by alex-turner on 2011-03-13
Hey Guys,

I've been running ubuntu from 9.04 now and all has been well until the other day. I went to upgrade, and stupidly did a apt-get dist-upgrade which took me to 11.04 - which is a little too alpha for my liking.

Never the less I recovered my data onto a USB disk and reinstalled 10.10. Since then I've reinstalled 5 times 10.10 and 10.04 with no luck. After each fresh install the computer will run for 30 minutes to an hour then just freeze. 

I'm running a Lenovo T410 and to be honest I'd rather run Windows ME or 95 without the service packs. Can someone please help me out, I cant install Windows and I'm computerless here.

Alex

---

### Post by Hedgehog1 on 2011-03-13
Alex,

I think getting you to the 10.04.2 long term support would be best.

I think we need to get a look at your disk partition layout to see what the various installs might have done.

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

p.s. Do you have your '/home' in its own partition?  It makes upgrades/downgrades easier.  Don't worry if you don't, we will get you there.

---

### Post by alex-turner on 2011-03-13
Hey Hedgehog,

Thanks for the quick reply. I've got a single partition with my / on it and a few gigs of swap space. I'll download 10.04 now and see how it goes.

Thanks man!
alex

---

### Post by Hedgehog1 on 2011-03-13
Alex,

Once 10.04.2 is installed, please menu to: System >> Administration >> System monitor.  Try to keep an eye on memory usage and swap space usage using System monitor.

I think your issue is not OS related as much as 'driver' memory leak related or 'application' memory leak related.

But that is a very rough guess right now.

***The Hedge***

:KS

---

