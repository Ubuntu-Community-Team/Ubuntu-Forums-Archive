---
title: "All sudo commands hang"
date: 2012-09-26
forum: General Help
---

### Post by jeffteel on 2012-09-26
I have a fresh install of Lubuntu 12.04. I accidentally wiped out a functional version. I installed it off a DVD, got networking going, then started adding a few apps. When I rebooted once, I noticed that networking was no longer functional. When trying to look into it, I noticed that every command I try to run as sudo no longer works. The terminal just hangs indefinitely.

Any ideas before I start all over?

---

### Post by AndyOpie150 on 2012-09-26
Personally I think you would be better off doing a fresh/clean install. That way you don't have any issue's later, after you have spent a lot of time trying to straighten it out. 

I know this is not what you asked, but it is the easiest and least time consuming option.

---

### Post by Rexilion on 2012-09-27
Please post the output of:

```
strace sudo <commandthatmakessudohang>
```

The 'strace' command is part of the 'strace' package, to install:

```
aptitude -y -R install strace
```

---

### Post by matt_symes on 2012-09-27
Hi

As an addendum to the post above, does this hang ?

```
strace -o ~/sudotrace.txt sudo -i 
```

If it does then post the output of ~/sudotrace.txt

Kind regards

---

