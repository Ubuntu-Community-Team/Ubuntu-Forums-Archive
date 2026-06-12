---
title: "Ubuntu apt mirror"
date: 2010-06-17
forum: General Help
---

### Post by andrewklau on 2010-06-17
Hello,

I run multiple Ubuntu desktops and laptops at home including one headless Ubuntu box which I use as my homeserver.

Updates are often as we all know, I've been thinking about making an apt mirror for my home. I'm AU where bandwidth is expensive so it'll save me a ton of bandwidth only downloading the updates once.

My two questions are:

1. Is this tutorial still up to date, if not could someone point me in the right direction :)
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

2. Will the apt mirror download all updates that are regulated, or only the ones I already download. For example, if I don't use MySQL on any of my computers and therefor don't need to download that update will my mirror waste my bandwidth to cache this update into its HDD space or will it exclude this.

Looking forward to some replies. Thanks!

---

### Post by dcstar on 2010-06-17
> **andrewklau said:**
> 
........
Updates are often as we all know, I've been thinking about making an apt mirror for my home. I'm AU where bandwidth is expensive so it'll save me a ton of bandwidth only downloading the updates once.
........

Many good ISPs in Australia host Ubuntu repositories that are free to download for customers, check the Software Sources list to see if your ISP is one of them.

---

### Post by andrewklau on 2010-06-17
Thanks though, however my ISP doesnt have that unfortunately. :(

Does anyone know another whether they have a solution for me?
Thanks.

---

### Post by bryanl on 2010-06-17
one approach would be to use apt-cacher. see the [ how to ](http://ubuntuforums.org/showthread.php?t=564301) in these forums or do a search for apt-cache.

this method doesn't try to replicate the entire repository. It only caches the packages requested when they are first requested. Machines later requesting that package have it available locally.

---

### Post by gmargo on 2010-06-17
I run an **approx** caching server on one of my machines, and all the other machines (real and virtual) are configured to go through it.  .deb packages get downloaded on demand then cached.

[http://packages.ubuntu.com/lucid/approx](http://packages.ubuntu.com/lucid/approx)

---

### Post by andrewklau on 2010-06-17
THANK YOU!!

That was exactly what I was looking for.

---

