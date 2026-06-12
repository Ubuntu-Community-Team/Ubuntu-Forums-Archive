---
title: "Faster alternatives to 'dd'"
date: 2010-01-31
forum: General Help
---

### Post by Jags_FL on 2010-01-31
Is there any faster alternative to 'dd' out there ? As DBAN doesn't work on SATA drives and dd takes forever...

Many thanks.

---

### Post by Xbehave on 2010-01-31
No, dd works as fast as it can there is no way to make a low level copy any faster

What are you trying to do?

---

### Post by Jags_FL on 2010-01-31
@ Xbehave

thanks for the reply. I frequently erases hard drives before installing new OSes.

---

### Post by FuturePilot on 2010-01-31
Increasing the blocksize that dd uses should make it a little faster.

---

### Post by Jags_FL on 2010-01-31
@ FuturePilot

how can I modify this 

```
dd if=/dev/zero  of=/dev/sdx
```

to increase the block size please... and what's the max it can be

---

### Post by Xbehave on 2010-01-31
> **Jags_FL said:**
> @ Xbehave

thanks for the reply. I frequently erases hard drives before installing new OSes.
Wiping the hard drive (e.g filling it with 1s,0s,random data) takes a  long time.
Are you sure you need to wipe the drive? (e.g just reformating isn't enough)
If you are then i don't think there is any tool faster than dd, but you should follow FuturePilot's advice and use a big blocksize (i think 512k should be enough but find a good guide on drive wiping and it'll know better than me)

edit: [this guide]("http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux") recommends 
```
dd if=/dev/zero of=/dev/sdx bs=1M
```

---

### Post by Jags_FL on 2010-01-31
Xbehave & FuturePilot

guys many thanks for your quick replies...

---

### Post by cariboo on 2010-01-31
Moved to General Help, where more users can benefit from this info.

---

