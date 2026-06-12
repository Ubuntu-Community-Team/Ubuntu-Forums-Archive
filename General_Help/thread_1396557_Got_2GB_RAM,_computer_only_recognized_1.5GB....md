---
title: "Got 2GB RAM, computer only recognized 1.5GB..."
date: 2010-02-02
forum: General Help
---

### Post by TheNessus on 2010-02-02
I got an nVidia 8400M G, on a lappy.(Fujitzu Esprimo v6515)   Is this normal? How do I get it to recognize the missing 500mb?

---

### Post by bluefrog on 2010-02-02
memtest to check if your RAM is all good

---

### Post by oni5115 on 2010-02-02
Not entirely sure, but it's probably the same thing that happened to me.  Linux takes what it needs for the kernel, and doesn't show that as existing, since it is used by the kernel. 

So even though I have 6 Gb ram, it only shows that I have 5.84 Gb.  Maybe this is what is happening?

I know I was confused too.  I hadn't remembered earlier versions of linux doing this, though maybe they did and I never noticed until now.

---

### Post by audiomick on 2010-02-02
I've read of similar things.
I think
```
top
```
shows you a fairly accurate picture of what is happening.

---

### Post by SoFl W on 2010-02-02
Is it shared memory?  Is the video taking up any memory?

---

### Post by TheNessus on 2010-02-02
> **SoFl W said:**
> Is it shared memory?Is the video taking up any memory?

how do I check?


top shows:   top - 16:05:45 up 14:45,  2 users,  load average: 0.02, 0.10, 0.11 Tasks: 147 total,   1 running, 146 sleeping,   0 stopped,   0 zombie Cpu(s):  5.5%us,  2.6%sy,  0.0%ni, 91.9%id,  0.0%wa,  0.0%hi,  0.0%si,   Mem:   1542952k total,  1182536k used,   360416k free,   214644k buffers Swap:  4514224k total,        0k used,  4514224k free,   504660k cached


I will run memtest now

---

### Post by philinux on 2010-02-02
Post back the output of this.

```
free -m
```

^^ and put code tags around the results.

---

### Post by kindofabuzz on 2010-02-02
The file system itself uses space.

---

### Post by philinux on 2010-02-02
> **kindofabuzz said:**
> The file system itself uses space.

Thats on the hard drive when formatting it reserves I think 5%.

---

### Post by audiomick on 2010-02-02
> **kindofabuzz said:**
> The file system itself uses space.

On the drive, sure, but not in RAM, does it?

---

### Post by philinux on 2010-02-02
According to the net this graphics card has 256 meg of ram but I think it can reserve another 512 meg from system memory. 

That would explain the 0.5 meg difference.

Windows would just report 2gig ram. Linux tells the truth. ;)

---

### Post by TheNessus on 2010-02-02
> **philinux said:**
> According to the net this graphics card has 256 meg of ram but I think it can reserve another 512 meg from system memory. 

That would explain the 0.5 meg difference.

Windows would just report 2gig ram. Linux tells the truth. ;)

Hmm, is there any way to make it reserve less, or none? I don't use graphics extensively other than compiz, no HD vids either.

free -m shows:
```

             total       used       free     shared    buffers     cached
Mem:          1506        703        803          0         95        286
-/+ buffers/cache:        321       1184
Swap:         4408          0       4408
```
I have used the liveCD (Karmic alpha) for memtest, it showed no errors, but when I tried to do the mem size test it crashed.

---

### Post by philinux on 2010-02-02
> **TheNessus said:**
> Hmm, is there any way to make it reserve less, or none? I don't use graphics extensively other than compiz, no HD vids either.

free -m shows:
```

             total       used       free     shared    buffers     cached
Mem:          1506        703        803          0         95        286
-/+ buffers/cache:        **[COLOR="Red"]321[/COLOR]**       1184
Swap:         4408          0       4408
```


You'd have to ask nvidia support. However I wouldn't worry. Your system at the time you posted this is only using 321 meg of ram. I've never seen mine go above 650meg except when I ran win 7 in virtualbox.

---

### Post by TheNessus on 2010-02-02
> **philinux said:**
> I've never seen mine go above 650meg except when I ran win 7 in virtualbox.
that is exactly why I'm worried about ram. Haven't for all this time with my computer, but I just need to use it more frequently now than before. 

Thanks everyone, though.

---

