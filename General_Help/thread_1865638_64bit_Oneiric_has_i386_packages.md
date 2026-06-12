---
title: "64bit Oneiric has i386 packages?"
date: 2011-10-20
forum: General Help
---

### Post by lykwydchykyn on 2011-10-20
I upgraded my 64bit natty desktop to oneiric.  I use a local apt-mirror repository to do upgrades, but whenever I do an apt update, I find that it's looking for i386 indexes.

So I added i386 repositories to my apt-mirror, and now updates are working, but apparently I have packages from both repos available now.  

I never needed i386 repos with natty, what's going on here??

What makes this extra frustrating is that aptitude (which I prefer for pkg mgt) shows an entry for both 64bit and i386, but doesn't tell me which is which; and of course the two conflict, which leads to lovely disasters in dependency handling.

I tried changing "deb" in my sources.list to "deb-amd64" (syntax from apt-mirror), but apparently that doesn't work for apt.

Do I really need both sets of packages in my package manager??

---

### Post by lykwydchykyn on 2011-10-20
Ah ok, here's the bug:

[https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768)

---

