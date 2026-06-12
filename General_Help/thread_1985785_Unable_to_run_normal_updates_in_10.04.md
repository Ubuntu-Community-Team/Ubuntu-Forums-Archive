---
title: "Unable to run normal updates in 10.04"
date: 2012-05-23
forum: General Help
---

### Post by dbclinton on 2012-05-23
Hi,
I'm running 10.04 LTS (which is supposed to be supported until April, 2013) and I am now unable to run normal updates. When trying (using the Update Manager GUI), I am told:
> Not all updates can be installed.
Run a partial upgrade, to install as many updates as possible.
...I hit the "Close" button rather than the "Partial Upgrade" for two reasons: 
One, I don't WANT to upgrade,
Two, I've heard that the partial upgrade is likely to break critical packages.
Does anyone have any idea how to fix this?
Thanks,
David

---

### Post by blackbird34 on 2012-05-23
"Partial upgrade" refers to updating your packages, as in the terminal command "sudo apt-get upgrade", which updates all your packages to the latest version available for your version of Ubuntu.
Thus "Partial Upgrade" does not mean you are suddenly going to end up with Ubuntu 10.10 or 12.04, it should be perfectly safe to go ahead.

---

### Post by dbclinton on 2012-05-23
Thanks.
I'm still a bit nervous about a partial upgrade. See this...

[http://ubuntuforums.org/showthread.php?t=1751299]("http://ubuntuforums.org/showthread.php?t=1751299")

---

### Post by blackbird34 on 2012-05-24
Oh right. But it looks like that post is about the development branch, doesn't it ?

---

### Post by dcstar on 2012-05-24
> **blackbird34 said:**
> "Partial upgrade" refers to updating your packages, as in the terminal command "sudo apt-get upgrade", which updates all your packages to the latest version available for your version of Ubuntu.
Thus "Partial Upgrade" does not mean you are suddenly going to end up with Ubuntu 10.10 or 12.04, it should be perfectly safe to go ahead.

+1 There is no issue here except user paranoia.

---

### Post by dbclinton on 2012-05-24
Well, ok. I'll give it a try. But if anything happens I will know who to blame... :)
Thanks for your help

---

