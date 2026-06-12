---
title: "/etc/rc.local not firing"
date: 2012-03-29
forum: General Help
---

### Post by Billy Ng on 2012-03-29
Title says it all.  Finished installing XUbuntu (11.10) a couple of hours ago on my HP G60-458DX laptop.  It took me a while, but I finally found a fix for turning off tap-to-click on my Synaptics touchpad:  ```
/usr/bin/synclient TapButton1=0
```

That works great as either me or root (sudo), but when I add that line to my /etc/rc.local ... it doesn't take affect after a reboot.  Checked the execution perms on rc.local, checked my syntax - everything good.  If I run /etc/rc.local manually, it does what it's supposed to, this leads me to believe that /etc/rc.local isn't being fired off on init.  /etc/rc2.d/ has an S99rc.local file that by all looks, should get kicked off by init, but apparently isn't.

Any thoughts?

On a positive note - at the same time I swapped out the drive for a Crucial M4 64GB SSD .... whew!  Bootup time is less than 20 seconds and that's including the 14 or so seconds it takes to get through the bios.  This should give you a clear picture of just how fast this thing is:
```
$ time sudo find / -type f -name thisthingisfast
[sudo] password for billy: 

real	0m7.811s
user	0m0.524s
sys	0m1.228s

```

---

### Post by Toz on 2012-03-29
That command won't work in /etc/rc.local because X needs to be up and running for it to take effect. Try putting it in your autostart list as:
```
bash -c "/usr/bin/synclient TapButton1=0"
```

---

### Post by Billy Ng on 2012-03-30
Thanks Toz.  For the record, I only needed to put ```
/usr/bin/synclient TapButton1=0
``` in autostart to get it to work, but get it to work it did, thank you.

For posterity sake, in case anyone finds this in the future:  To find autostart in xfce (XUbuntu 11.10 in my case):

Apps Menu => Settings => Settings Manager => Session and Startup

---

