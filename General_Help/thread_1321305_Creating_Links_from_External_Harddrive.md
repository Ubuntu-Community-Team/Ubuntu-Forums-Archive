---
title: "Creating Links from External Harddrive"
date: 2009-11-09
forum: General Help
---

### Post by jdorenbush on 2009-11-09
How do I create a link (shortcut) from a folder within an external harrdrive? 

I am getting an error: "Error making symbolic link: Operation not permitted"

Do I need to format the drive as NTFS or something?

---

### Post by cariboo on 2009-11-09
Are you using sudo when you create the link eg:

```
sudo ln -s /media/storage storage
```

---

### Post by jdorenbush on 2009-11-09
> **cariboo907 said:**
> Are you using sudo when you create the link eg:

```
sudo ln -s /media/storage storage
```

I was just right clicking and hitting 'Make Link' for a particular folder in my external harddrive that I wanted to create a link to place on my desktop.

Also noticed that my external harddive is always in all caps whereas my DVD drive and other filesystems are not. I tried changing via GParted but that had no effect.

---

