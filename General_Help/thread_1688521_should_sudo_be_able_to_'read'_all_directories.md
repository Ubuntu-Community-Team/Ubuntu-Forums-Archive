---
title: "should sudo be able to 'read' all directories?"
date: 2011-02-15
forum: General Help
---

### Post by daweefolk on 2011-02-15
I just installed sudo (I have slackware but always got better help here ;)) and I tried doing a ```
sudo du /
``` to see if I could get a general size estimate of all the directories and despite running it sudo I still was told "Cannot read directory" on some of the directories on my pc. should sudo have made it so I could read them all?

---

### Post by hawkmage on 2011-02-15
Are they something like "/proc/24800/task/24800/fd/3"?

Many times directoryies under /proc can appear and then go away so that du or other utilities see the directory but by the time it does to look at it it no longer there.

---

### Post by daweefolk on 2011-02-16
Okay, that explains that, thanks. The thing I was more wondering about though, is when I do a sudo du / anything in root's home, var, etc, and usr all spit out "permission denied".
shouldn't sudo override that?

---

### Post by hawkmage on 2011-02-16
Yes sudo should allow you access to those directories.

What do you get if you run:
```
sudo -l
```

---

### Post by daweefolk on 2011-02-16
```
User jordan may run the following commands on this host:
(ALL) ALL
```

---

### Post by hawkmage on 2011-02-16
OK that is good.  What about the output from this:
```
ls -l `which sudo`
```
(Those are back ticks not single quotes.)

---

### Post by daweefolk on 2011-02-16
-rws--x--x 1 root bin 90400 2006-02-06 13:00 /usr/bin/sudo

---

### Post by hawkmage on 2011-02-16
OK, the set UID bit is properly set on the executable and is owned by root so I am not sure why it is not working.

---

### Post by daweefolk on 2011-02-17
Also, from my "jordan" account I'm unable to run any programs in /sbin with sudo unless I make a symlink to them in /bin

---

### Post by daweefolk on 2011-02-17
Problem solved. I realized I'd only been hibernating my computer every time I finished. I did a reboot and WHAM sudo works like a charm.

---

### Post by asmoore82 on 2011-02-17
> **daweefolk said:**
> Also, from my "jordan" account I'm unable to run any programs in /sbin with sudo unless I make a symlink to them in /bin

You shouldn't do this.
If you need to run programs in /sbin, add /sbin to your PATH.

I do not hold Slackware in high esteem.

---

### Post by daweefolk on 2011-02-17
> **asmoore82 said:**
> You shouldn't do this.
If you need to run programs in /sbin, add /sbin to your PATH.

I do not hold Slackware in high esteem.

I hadn't even thought of adding /sbin to my PATH until now, I suppose that makes a lot more sense now doesn't it?

---

### Post by pekon on 2011-02-17
Some users might not want that "normal" users hv access to all utilities / bin commands available (as this may lead to some security loop holes). 
example: "fdisk" in some systems is present only in /sbin

That is why most administrator related binaries are kept in /sbin
While general ones are kept in /bin

Incase you want to use all /sbin utilities .. why not add urself to "admin" group

---

### Post by daweefolk on 2011-02-17
I guess I never considered doing that because I had let other people use my computer in the past. They never want it now that my wm is ratpoison though :) so I'll just do that.

---

