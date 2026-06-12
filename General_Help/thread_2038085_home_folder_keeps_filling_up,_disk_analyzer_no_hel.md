---
title: "home folder keeps filling up, disk analyzer no help"
date: 2012-08-05
forum: General Help
---

### Post by linuxgrrl on 2012-08-05
hi,
My home partition is 37 GB, and the only things I have (consciously) stored there are a few documents and files, nothing that should be anywhere near that size.  But the /home/ partition is continually showing 100% full and I keep geting error messages about it.  

When I run disk usage analyzer, it indeed shows /home/mary as "red",but the sub items underneath it are all of modest size and do not add to more than 3 GB. I deleted a bunch of photos, which cleared some space but within a few minutes it was full again.

Help?

---

### Post by steeldriver on 2012-08-05
It sounds like you've got a log file that's growing - there have been several recent reports about users' .xsession-errors files doing that, so that's one place to look

```
ls -l /home/*user*/.xsession-errors
```Beyond that, here are a couple of one liners you can try - not sure if they'll find anything different than the GUI usage analyzer though

Find the top 10 subdirectories by disk usage:
```
sudo du -h /home |sort -hr|head -10
```Find any individual regular file bigger than 100MB
```
sudo find /home -type f -size +100M
```

---

### Post by dcstar on 2012-08-08
> **linuxgrrl said:**
> hi,
My home partition is 37 GB, and the only things I have (consciously) stored there are a few documents and files, nothing that should be anywhere near that size.  But the /home/ partition is continually showing 100% full and I keep geting error messages about it.  

When I run disk usage analyzer, it indeed shows /home/mary as "red",but the sub items underneath it are all of modest size and do not add to more than 3 GB. I deleted a bunch of photos, which cleared some space but within a few minutes it was full again.

Help?
Disk Analyzer runs under user privileges, do this:
```
gksudo baobab
```

You may well find log files filling up the system - if so then find the problem filling the logs.

---

