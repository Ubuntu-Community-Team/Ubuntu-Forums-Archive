---
title: "Used Remastersys and made a custom iso of my Ubuntu - but now left with a 1.5GB solid"
date: 2012-04-18
forum: General Help
---

### Post by AlexOnVinyl on 2012-04-18
**Update: I tried to recreate my swap - after recreating it and editing fstab - and rebooting I ran:**

```
swapon -s
```

and found this:
> alex@griever:~$ swapon -s
    Filename				Type		Size	Used	Priority
    /dev/zram0                              partition	1418760	0	100

which explains the solid state drive in the disk utility, now how do I get rid of it and get my old Swap back, because currently, this is what my old swap looks like:

[IMG]http://i.stack.imgur.com/hfbNY.png[/IMG]

all the unallocated data - and still cant get rid of the other Solid state swap

---------------------------------------------------------------------------------------------------------

So what exactly is going on here... I hit the ```
`clear
```` dialogue on my Remastersys and it cleared out everything, but now I'm stuck with this:

[IMG]http://i.stack.imgur.com/nLD8m.png[/IMG]

But my Gparted Shows nothing out of the ordinary...

The 15GB is reserved for a Debian install I plan to dual-boot with - so that's not part of the issue.

[IMG]http://i.stack.imgur.com/sszCk.png[/IMG]

---

### Post by HiImTye on 2012-04-18
you are looking at /dev/sda in GParted, select a different device with the drop down at the top right

---

### Post by AlexOnVinyl on 2012-04-18
> **HiImTye said:**
> you are looking at /dev/sda in GParted, select a different device with the drop down at the top right

These are the only 2 to choose from - my main drive and my external drive:

External: [IMG]http://i.imgur.com/T1oiD.png[/IMG]
Internal: [IMG]http://i.imgur.com/KUWBN.png[/IMG]

---

### Post by AlexOnVinyl on 2012-04-18
> **HiImTye said:**
> you are looking at /dev/sda in GParted, select a different device with the drop down at the top right

Okay I recreated my Swap but when I rebooted after editing fstab

I found this:


```
alex@griever:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/zram0                              partition	1418760	0	100
```

Which explains that solid state that Remastersys created..

Now how do I restore my default Swap? and get rid of this one?

---

### Post by AlexOnVinyl on 2012-04-18
Bump

---

