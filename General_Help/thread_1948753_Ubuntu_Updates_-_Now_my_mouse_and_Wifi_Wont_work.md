---
title: "Ubuntu Updates - Now my mouse and Wifi Wont work"
date: 2012-03-28
forum: General Help
---

### Post by SS113 on 2012-03-28
Hello everybody!

Pretty new to Ubuntu (3 months now) so bear with me.

I was working on my laptop and the regular Ubuntu Updates popped up.  I closed everything down and I started to download the updates.  I put in my password but this time it never really started downloading the updates like before.  I waited and waited but nothing.  I tried closing it and starting the updates again but something told me apt-get was running already.  

I tried restarting the computer and now my mouse wont work at all (even the left/right buttons) and my Wifi won't connect.  I don't know too much my way around Ubuntu with just the keyboard so what can I do at this point?  

I also noticed that the computer seems VERY sluggish now too.. 

Can I somehow roll back any changes it did or maybe the Windows equivalent of "safe-mode"?

My laptop:

Ubuntu 11.10
Lenovo Thinkpad T420 - Core i5, 8GB Ram, 500GB HDD

Thank for any help!

---

### Post by SS113 on 2012-03-28
I shoulda Googled first :lolflag:

After I restarted I went back to the update manager and it told me this:

> It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

After a quick search on that,

I ran 

```
$ sudo dpkg --configure -a
```

and restarted... now everything's back to normal, my mouse works, wifi works and it's snappy like before!

Thanks anyway guys! I hope this thread helps somebody else in the future!

---

