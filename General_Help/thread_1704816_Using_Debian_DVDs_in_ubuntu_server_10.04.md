---
title: "Using Debian DVDs in ubuntu server 10.04"
date: 2011-03-11
forum: General Help
---

### Post by Farrukhjon on 2011-03-11
Hi guys! Help me, can i use all packages in Debian 5 Lenny DVDs (1-6) without any problem in my Ubuntu Server 10.04? For example using apt-cdrom and apt-update, apt-install xxxx ?. Would't affect these actions for potential errors?
Thank in advance :)

---

### Post by lithopsian on 2011-03-11
You can try :)  Expect glitches.  Some of the builds are slightly different and some of the dependencies will be different too.

---

### Post by Farrukhjon on 2011-03-11
How to check that dependency is different and system broken, because when i install mc its works and aptitude install -f not print any wrong o errors

---

### Post by lithopsian on 2011-03-11
You **can't** check that the dependencies are different.  Debian builds a set of dependencies for Debian and Ubuntu builds a set for Ubuntu.  They are similar but not the same.  Any check is simply checking the reported dependency in each repository but if they don't match then you don't know you have a problem.  BTW, a good way to check consistency is "apt-get check", but if you've mixed repositories then it doesn't guarantee anything.

Same with the builds.  You may or may not be getting the same version from Lenny as from Lucid, and it may have been compiled against different headers.  So it may or may not work, and the only way to tell is to run it.  I suggest that most of the time you won't see any problems, but sometimes you will and when you do your whole package installation could be totally hosed and unrecoverable.

So you can try this, and if you're really hot stuff with dpkg you can get away with all sorts of stuff that you shouldn't even try, but the fact that you have to ask the question suggests you may be getting out of your depth.  The usual advice is not to even try mixing distros if you value stability.

---

### Post by tgalati4 on 2011-03-11
It will work fine until it breaks.

And you get to keep both pieces.

---

### Post by dcstar on 2011-03-12
> **tgalati4 said:**
> It will work fine until it breaks.


Which usually won't take long. It is a pretty stupid thing to do as there is nothing wrong with the correct Ubuntu packages.

---

