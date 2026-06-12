---
title: "dpkg --get-selections problem"
date: 2010-11-12
forum: General Help
---

### Post by holocene on 2010-11-12
Hi,

I was messing with dpkg, attempting to understand how to use it to document installed packages, save a list of packages, and then reinstall those packages from a text file.

The command I ran that I should not have, I believe, is
dpkg --clear-selections

Because when I run 
dpkg --get-selections

most say to deinstall.

How do I return my system to the prior state, of just installed?

I am not even sure if this is a problem, anyway. But, better safe than sorry.

any help appreciated.
Steve.

---

### Post by zvacet on 2010-11-13
If you want to know witch packages you installed and want it install again then type 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```

You will find text file in your home directory.Save that file on usb ( or mail to yourself) and put it on other machine ( in home directory) and run

```
sudo xargs aptitude --schedule-only install < my-packages 
sudo aptitude install
```

---

