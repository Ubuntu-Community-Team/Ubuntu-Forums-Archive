---
title: "[Linux Mint 9] Limited Space Remaining Error Message"
date: 2010-12-13
forum: General Help
---

### Post by liquidfunk on 2010-12-13
So I installed Linux Mint 9 LTS onto the family computer last weekend, everything went okay apart from today when suddenly it displays a low disk space message.

The machine has a 250Gb HDD, and has the base install of Mint, plus Dropbox and Google Chrome. (Dropbox has about 500Mb in it). That's it. 

The disk usage analyzer tells me that /home is 100% full, yet when I look into each dropdown there is barely enough to make 2Gb of usage. (The most being Dropbox). 

Any idea of what's happened?

---

### Post by lrgmmc on 2010-12-13
how big is your home prtition?

---

### Post by liquidfunk on 2010-12-13
211GiB

---

### Post by lrgmmc on 2010-12-14
```
sudo du -h --max-depth=1 /home
```
that will tell you how much space each user is using. good start for tracking down where your space is.

---

### Post by liquidfunk on 2010-12-15
Thanks, but the trouble is, there is only one user on the machine, my Mum. 

I know she hasn't downloaded anything, because she doesn't know how to.

---

