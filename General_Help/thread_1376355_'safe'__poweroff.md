---
title: "'safe'  poweroff?"
date: 2010-01-09
forum: General Help
---

### Post by Exonimus on 2010-01-09
Hi guys,

Due to some reason not known to me at this moment, my regular shutdown doesn't work. It freezes on disabling the swap file and doesn't do anything. Now, until that problem is solved, I need a way to properly shutdown. I found one, which is poweroff -f, but it is hardly graceful, and would amount to 'flipping the switch'  I guess. The other is hibernate, which is what I now use. This does work, but I rather completely shut down the system. For one, regular boot is quicker than resuming from hibernate.

My main question is: is there any way to make the poweroff -f command, e.g. combined with manually disabling the swap file or whatever,"safe?" as in, I can imagine a sudden power off meaning more chance of damage to the HD, which I don't want.

Thanks for any replies.

---

### Post by OldGrantonian on 2010-01-09
Here are a couple of links which I hope might help:

[http://ubuntuforums.org/showthread.php?t=846172](http://ubuntuforums.org/showthread.php?t=846172)

[http://ubuntuforums.org/showthread.php?p=8632358#post8632358](http://ubuntuforums.org/showthread.php?p=8632358#post8632358)
.

---

### Post by Exonimus on 2010-01-09
Thanks for the suggestions, but my problems are, sadly, not solved.

As said, until I find the solution, I'd just like to know if it's safe to actually use poweroff -f. I saw (when searching) that someone used a script to A: poweroff -f but before he issued that command, he used 'sync' and manually stopped using the swap file. 

How safe would one consider shutting down that way, in respect to potentially damaging the hard drive?

---

### Post by NoaHall on 2010-01-09
Try this - 
```
sudo shutdown -h now
```

---

### Post by Exonimus on 2010-01-09
that gives me the same problem

---

### Post by NoaHall on 2010-01-09
> **Exonimus said:**
> that gives me the same problem

Using it that way is safe.
If you want, you could do ```
sudo swapoff
``` first.

---

### Post by ratcheer on 2010-01-09
I use: sudo init 0

Tim

---

