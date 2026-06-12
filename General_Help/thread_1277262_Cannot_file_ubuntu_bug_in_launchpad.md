---
title: "Cannot file ubuntu bug in launchpad"
date: 2009-09-28
forum: General Help
---

### Post by jarl on 2009-09-28
I cannot file a new bug using launchpad.

I try to go to 
[https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

But I am redirected to 
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

How do I submit a new bug for ubuntu. I would like to request new software, namely clang ([http://clang.llvm.org/](http://clang.llvm.org/))

Jarl

---

### Post by zeroseven0183 on 2009-09-28
You'll find in that page the link to where you can file a bug in Launchpad.

Copy this link and change the PACKAGENAME to the specific source package you want to file a bug: [URL="https://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect"]https://bugs.launchpad.net/ubuntu/+source/**PACKAGENAME**/+filebug?no-redirect
[/URL] 
For example, [https://bugs.launchpad.net/ubuntu/+source/**empathy**/+filebug?no-redirect]("https://bugs.launchpad.net/ubuntu/+source/empathy/+filebug?no-redirect")


or simply add **?no-redirect** on the first link you posted

[https://bugs.launchpad.net/ubuntu/+filebug?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug?no-redirect)

---

### Post by wojox on 2009-09-28
You should use apport to file bugs. I see a lot of people filing at launchpad just to have them put back into the Ubuntu answers . 

Hit Ctrl + F2 

Type: ubuntu-bug <package-name>

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by zeroseven0183 on 2009-09-28
> **wojox said:**
> You should use apport to file bugs. I see a lot of people filing at launchpad just to have them put back into the Ubuntu answers . 

Hit Ctrl + F2 

Type: ubuntu-bug <package-name>

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

Correction. That should be [B]Alt + F2  :)
[/B]

---

### Post by wojox on 2009-09-28
> **zeroseven0183 said:**
> Correction. That should be [B]Alt + F2  :)
[/B]

Good eye. Thanks :)

---

### Post by MoebusNet on 2009-09-28
> **wojox said:**
> You should use apport to file bugs. I see a lot of people filing at launchpad just to have them put back into the Ubuntu answers . 

Hit Ctrl + F2 

Type: ubuntu-bug <package-name>

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

That works fine if Apport isn't broken, which it is in Ubuntu Karmic alpha 6.

I'm trying to report a bug that prevents Karmic from ever reaching the login screen. I can boot Karmic the first time of the day, then cannot boot again if I shut down. This may be related to the bug that was reported in alpha 5 where the file system incorrectly time/date stamps in GMT rather than local, resulting in a file dated in the future.

I wonder if they're just swamped by bugs right now?

---

