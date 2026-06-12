---
title: "http://archive.canonical.com/ubuntu karmic partner"
date: 2009-11-27
forum: General Help
---

### Post by Richiegs on 2009-11-27
I am new to Ubuntu and am using 9.10. Under Software Sources, there is a listing called [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner. I don't know what it is for and should I put a check mark in the box next to it. Thank you for your help

---

### Post by slakkie on 2009-11-27
The repo is used for flash, among others:

[http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/](http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/)

See this link for more information about repo's: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by audiomick on 2009-11-27
Hallo. That is the repository for software provided by partners of canonical. If you have not added anything to your standard Ubuntu installation, you don't need to activate it, but it will not hurt anything if you activate it and don't need it.

---

### Post by el cameleon on 2009-12-04
I have activated this repository but cannot find acroread in the list of available program. Do I forget something?

---

### Post by egalvan on 2009-12-04
You probably need to refresh/reload the sources.

there is a button for this..

under Update Manager, it's called "check"

under Synaptic, it's called "reload"

---

### Post by el cameleon on 2009-12-04
These possibilities do not exist anymore in the new Software Center in Karmic.

---

### Post by egalvan on 2009-12-04
> **el cameleon said:**
> These possibilities do not exist anymore in the new Software Center in Karmic.

OK, but did you try running Synaptic?
And if you don't have it installed,

then open a terminal and run this

```
sudo apt-get update

```

---

### Post by audiomick on 2009-12-04
I think acroread is at medibuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I'm pretty sure it used to be, anyway.

---

### Post by egalvan on 2009-12-04
[http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html](http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html)

---

### Post by el cameleon on 2009-12-04
> **egalvan said:**
> [http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html](http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html)
thanks, this is the final answer, althought I don't understand why it is not shown into the software center, ```
apt-get install acroread
``` close the issue.

---

