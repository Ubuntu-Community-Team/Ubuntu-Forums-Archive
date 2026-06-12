---
title: "Missing Space on my ext4 partition"
date: 2011-04-01
forum: General Help
---

### Post by Amctict on 2011-04-01
A couple of days ago, I hooked an external hard drive up to my laptop and transfered a bunch of files from an old Apple laptop. 

I was pretty sure that I would have enough free HD space, so I was surprised to get a warning that my HD storage space was running low. Disk Usage Analyzer and all other programs tell me that I'm using 71.5 of 77 GB. But that didn't seem right. GParted shows that my Ubuntu partition is actually 120 GB, which is what I thought it was in the first place. And still, it's telling me that I'm using 113 GB, which seems like way too much (I wasn't really keeping track of the amount I transfered, and yeah, that's my bad-- I should have known better).

But is there a reason for the different amounts of HD space these two programs are showing? Here's a screenshot of the two programs on my desktop.

Any help would be appreciated. Thanks.

---

### Post by seawolf167 on 2011-04-01
Aside from the differences between base2 and base10 (i.e. 1TB = 931GB), ext saves 5% as disk overhead.

I know you can turn it off, but I haven't done it in a while and can't remember how to do it.

EDIT: just answered this in a different post so I went and Googled it - [here]("http://www.lisnichenko.com/articles/ext3-file-system-overhead-disclosed-part-1.html") is a link with an explanation as well as the command

---

### Post by matt_symes on 2011-04-01
Hi

> **seawolf167 said:**
> Aside from the differences between base2 and base10 (i.e. 1TB = 931GB), ext saves 5% as disk overhead.

I know you can turn it off, but I haven't done it in a while and can't remember how to do it.

IIRC, You use tune2fs to turn it off.

```
man tune2fs
```

Kind regards

---

### Post by Amctict on 2011-04-01
Tune2fs seems to be working. Thanks!

---

