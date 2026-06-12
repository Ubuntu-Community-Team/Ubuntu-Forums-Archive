---
title: "alsamixer Error opening terminal: unknown."
date: 2011-05-01
forum: General Help
---

### Post by davidstoll on 2011-05-01
When I try to run alsamixer, I get this...

```
$ alsamixer 
Error opening terminal: unknown.
```

Any ideas?

Running 10.10 32bit, but may upgrade to 11.04.
This is a fresh install of 10.10.  Audio was fine until I had to re-install.  I don't remember doing any configuration for it when I installed before...hmmm

---

### Post by papibe on 2011-05-01
alsamixer is usually included in the alsa-utils package. Check if that is installed:
```
$ dpkg -l alsa-utils
```
if it's not, install it either using the Software Center, or like this:
```
$ sudo apt-get install alsa-utils
```
Regards.

---

### Post by davidstoll on 2011-05-01
it says that it's already installed

---

### Post by papibe on 2011-05-02
May be a path issue?
```
$ dpkg -L alsa-utils | grep alsamixer
/usr/share/man/man1/alsamixer.1.gz
/usr/bin/alsamixer

```
Try calling it directly:
```
$ /usr/bin/alsamixer
```
I hope it helps.

---

### Post by davidstoll on 2011-05-08
Actually, I did call it directly, but got the same issue.

Basically, the problem is that depending on the distro I use (10.04, 10.10, 11.04, etc), I get different problems.

So, I re-installed, but now I have an issue with being able to scan channels from a tv tuner (not related to this particular post, but it's a bit frustrating).

I hope that when we leave this "versioning" system, we'll not have these issues when attempting a new or re-install.




> **papibe said:**
> May be a path issue?
```
$ dpkg -L alsa-utils | grep alsamixer
/usr/share/man/man1/alsamixer.1.gz
/usr/bin/alsamixer

```
Try calling it directly:
```
$ /usr/bin/alsamixer
```
I hope it helps.

---

