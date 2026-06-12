---
title: "Error Message"
date: 2009-08-16
forum: General Help
---

### Post by iandev on 2009-08-16
I hope somebody can help me with this
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
I cannot run the package manager how do i get unmet dependencies for my packages

Many thanks Ian.

---

### Post by lessgov2007 on 2009-08-16
Not sure if this will work, but something to this effect. Try from a terminal window:


sudo apt-get check -f

I think that's right. I guess I go search...

Okay see this thread. I looks like it has some good info on the subject.  [http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

### Post by iandev on 2009-08-16
Just tried that it comes up with the same error thanks anyway.

---

### Post by lessgov2007 on 2009-08-16
> **iandev said:**
> Just tried that it comes up with the same error thanks anyway.
Did you read the thread I posted a link to? I scanned through it. It looks like it has some good info that might be helpful.

---

### Post by michy99 on 2009-08-16
Try this:```
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages
```

---

### Post by iandev on 2009-08-16
> **michy99 said:**
> Try this:```
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages
```
I did try it and it said no such file.

---

