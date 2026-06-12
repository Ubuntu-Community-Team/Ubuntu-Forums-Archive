---
title: "Root"
date: 2006-02-19
forum: General Help
---

### Post by jenkins_t on 2006-02-19
I recently installed Ubuntu on my hda. It never prompted me for a root password. What is it by default?


Thanks,
Travis

---

### Post by aysiu on 2006-02-19
There is no root password.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by RAOF on 2006-02-19
There is no root password by default - the root account is disabled.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) gives details and justification.

---

### Post by jpkotta on 2006-02-19
A random string.  In Ubuntu, you use sudo to do things as root.  If you must become root, ```
sudo su
```If sudo is broken, boot into single user mode and fix it.

---

### Post by jenkins_t on 2006-02-19
Wow that was fast response!

sudo su. got it.

I have come from Mepis, in Ubuntu, are all sites OK in sources.list to enable? Are some etch, or sid like?

---

### Post by RAOF on 2006-02-19
**Do not** put debian sources in sources.list, unless they're very specific-purpose.  Ubuntu packages use a subtly different naming scheme, and packages in general are **not** binary compatible with Debian ones.  It's possible for a Debian package to render your Ubuntu install totally broken - if it installs an update for a library that apt/dpkg depends on, you'll have no way to fix your install.

Sources like wine.sourceforge.net/apt are fine (although they also have a breezy repo), because they contain only the final package, no dependant libraries.  As long as you install no libraries from Debian sources, you are *reasonably* safe.

---

### Post by jenkins_t on 2006-02-19
I added rep from [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) and updated. All seems Ok! ver 5.1

BTw, have a tri boot laptop, XP, Mepis, now Ubuntu! Linux is awesome.

---

