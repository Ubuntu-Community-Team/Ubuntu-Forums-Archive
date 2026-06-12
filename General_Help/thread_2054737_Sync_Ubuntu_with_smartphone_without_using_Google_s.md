---
title: "Sync Ubuntu with smartphone without using Google serices? (or the cloud in general)"
date: 2012-09-07
forum: General Help
---

### Post by Adam's AI on 2012-09-07
Is there anyway to sync a smartphone with ubuntu without using google services or ubuntu one (or any other cloud service)?

Coming from using mainly Apple (but not iCloud), I am used to plugging in my smartphone and having contacts, music, apps, calendars all synced without having that info pushed through the cloud. Looking into switching full-time to ubuntu + android phone, I was genuinely surprised at how integrated it was with Google services. For someone who is a little wary of pushing all of my data through the cloud, is there anyway to sync this info through a desktop app(s)?

---

### Post by Adam's AI on 2012-09-08
I actually meant to post this in the General Help forum. I apologize for accidentally posting it here. Can someone delete this duplicate thread? The new post is [here]("http://ubuntuforums.org/showthread.php?t=2054738"). Sorry about that!

---

### Post by 2F4U on 2012-09-08
You can setup your own cloud service on a local machine with an application named ownCloud

[http://owncloud.org/features/](http://owncloud.org/features/)

---

### Post by Adam's AI on 2012-09-08
> **2F4U said:**
> You can setup your own cloud service on a local machine with an application named ownCloud

[http://owncloud.org/features/](http://owncloud.org/features/)

Thanks for the reply :) Interesting, I've heard of that one before. However, doesn't it still send files over the internet? Isn't there a way of just syncing over usb?

---

### Post by nothingspecial on 2012-09-08
*Thread moved to **General Help**.*

---

### Post by thnewguy on 2012-09-08
You could probably use rsync to transfer files between the two devices when the phone is physically plugged into your desktop. For example, if you plug in your phone and its file system gets mounted under the /media folder you could run something like

rsync -auv ~/Documents /media/phone/Documents
rsync -auv /media/phone/Documents ~/Documents

Check out the rsync manual page for examples.

---

