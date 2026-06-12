---
title: "simple-scan: created scans permissions too restrictive"
date: 2010-10-18
forum: General Help
---

### Post by imbjr on 2010-10-18
Like the title says: scan something, save image, place image on shared NFS partition, see if other users can read the file - no they cannot, because the file is rw only for the person who scanned the file.

Anyone else see this happen, or know of a way of having permissions change as a file is copied into a directory?

---

### Post by cheribibi on 2011-11-16
> **imbjr said:**
> Like the title says: scan something, save image, place image on shared NFS partition, see if other users can read the file - no they cannot, because the file is rw only for the person who scanned the file.

Anyone else see this happen, or know of a way of having permissions change as a file is copied into a directory?
Well... it's been a long time since you posted this, imbjr, but I face the same problem, and while I was searching for a solution on the net, I found your post.
I just posted a [question]("https://answers.launchpad.net/ubuntu/+source/simple-scan/+question/179010") on Ubuntu's launchpad related to simple-scan (in french and english), let's see if it gives something...

---

### Post by cheribibi on 2011-11-16
I've just been trying some other scan utilities and finally found that gscan2pdf stores pdf with -rw-rw-rw- permissions.

Gnome-scan seems not to be able to save as pdf, just png, (but with rw for all too).

---

### Post by imbjr on 2011-11-16
> **cheribibi said:**
> Well... it's been a long time since you posted this, imbjr, but I face the same problem, and while I was searching for a solution on the net, I found your post.
I just posted a [question]("https://answers.launchpad.net/ubuntu/+source/simple-scan/+question/179010") on Ubuntu's launchpad related to simple-scan (in french and english), let's see if it gives something...

Thanks for posting that to launchpad. I didn't realise you could do that.

---

