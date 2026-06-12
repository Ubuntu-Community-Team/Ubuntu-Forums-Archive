---
title: "Updating Issues"
date: 2010-12-13
forum: General Help
---

### Post by HoodedHooligan on 2010-12-13
First of let me say that I think my problem stems from a problem with my computer's hardware and not Ubuntu but I want to double check.

I have been running Ubuntu on my laptop since 9.10 by itself (not dualbooting Windows). I had no problems with it back then but I did notice that when I upgraded, not all the packages installed and I would get an error message saying so. I never thought much of it. The problem became apparent when upgrading from 9.10 to 10.4, I would get an error message everytime and the upgrade would be cancelled. This forced me to reinstall Ubuntu for both 10.04 and 10.10. As soon as I downloaded 10.10 I downloaded docky and chromium. Heres where my current problems arise:

- Docky (which worked in 10.04) wont work even after I download compiz.
- Every time i update the system, if i try to update chromium or anything else from google it cancels the upgrade.
- I tried using "sudo apt-get upgrade" in the terminal but i get
 "Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened."

Please help fix this. I am not afraid of the terminal...

---

### Post by argedion on 2010-12-13
I saw this the other day with someone else having some problems with updating/upgrading so this may work for you.

```
in not chroot use:
sudo -i
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
```

hope this will be able to help you resolve those issues.

---

### Post by HoodedHooligan on 2010-12-15
I put in "sudo i" then "apt-get autoclean" and I got the same message as before.

---

### Post by HoodedHooligan on 2010-12-24
I hope this topic isn't dead. I can no longer open the software center or any type of media player. All I can do now is going on the internet. I was thinking on reinstalling Ubuntu but this would be the 4th time I would have had to do this. There are to be a better solution, right?

---

### Post by HoodedHooligan on 2012-06-25
I learned it was a HDD issue, my new computers have no issues.

---

### Post by sffvba[e0rt on 2012-06-25
*Old thread **closed**.*


404

---

