---
title: "Skype &amp; 10.04 Repository?"
date: 2012-06-18
forum: General Help
---

### Post by jamesisin on 2012-06-18
I have been using this repository for Skype:

[http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/)

For whatever reason that's still back on version 2 point something or other.  Four is out and out of beta.

Is there a known good repository for 4 which will work on 10.04?

---

### Post by kostkon on 2012-06-18
SKype is also in the Partner repo:
```
apt-cache policy skype
skype:
  Installed: 4.0.0.7-1
  Candidate: 4.0.0.7-1
  Version table:
 *** 4.0.0.7-1 0
        100 /var/lib/dpkg/status
     2.2.0.35-0lucid1 0
        500 http://archive.canonical.com/ubuntu/ lucid/partner Packages
```
but it still offers the 2.2 version.

My suggestion: just download the deb from skype's website. It works just fine on 10.04.

Make sure that you first remove your previous version of skype. To be sure, give this line in a terminal:
```
sudo apt-get purge skype skype-bin skype-common
```
i.e. you may also have skype-bin or skype-common installed.

---

### Post by jamesisin on 2012-06-19
Sure I can load a .deb.  I was just hoping to find a repo which is kept up to date.

---

### Post by Paddy Landau on 2012-06-19
I read on the Skype forums that there is unlikely ever to be an official PPA, so you'd have to wait for Ubuntu to add it. That is unlikely to happen for 12.04 and before, but probably will happen for 12.10.

---

### Post by kostkon on 2012-06-19
> **Paddy Landau said:**
> I read on the Skype forums that there is unlikely ever to be an official PPA, so you'd have to wait for Ubuntu to add it. That is unlikely to happen for 12.04 and before, but probably will happen for 12.10.
Actually 3rd party vendors can push updates to their software that is in the Partner repo, like Adobe does, and Skype did in the past. But, it remains to be seen whether Skype will update their software to the new version 4.

---

