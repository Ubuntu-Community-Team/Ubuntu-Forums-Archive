---
title: "Just a Reminder"
date: 2011-05-29
forum: General Help
---

### Post by Billsey on 2011-05-29
A bit more than a week ago, my 10.04 machine ran into a problem with getting updated repo information. I discovered that, somehow, it had a hold-over from Jaunty. It was trying to get updates to the Jaunty backports repositories. I only solved it by using "sudo gedit /etc/apt/sources.list" and "sudo gedit /etc/apt/sources.list.save" to comment out the lines that reference the Jaunty backports repositories. Using the preferences editor to do the same thing had had no effect at all.

This might be reason for looking into whatever updating of the sources.list and sources.list.save files occurs during a distribution upgrade.

---

### Post by linuxinstalledfromhdd on 2011-05-29
I do not do upgrades anymore. It is so frustrating sometimes, even for an experienced user of Ubuntu. I do fresh installations only. If someone does an upgrade, you would need to "Trim" your source.list file each time.  And then readd your PPAs again.

---

### Post by drs305 on 2011-05-29
I'll tag on a bit. I'd recommend a newer version, but if you need or want to keep Jaunty and desire to access it's repositories, it's still possible. Note these repositories will not be updated with security or other patches.

Substitute the following in /etc/apt/sources.list:

> [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)

Example:
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty main restricted universe

---

