---
title: "How to use second hard drive with Ubuntu?"
date: 2011-07-09
forum: General Help
---

### Post by trizrK on 2011-07-09
Hello, i have a SATA drive for my main hard drive, and a 400 gb HDD with nothing on it. I was wondering how i could use it to save files from Ubuntu onto it.
Thank you in advance

---

### Post by wildmanne39 on 2011-07-09
> **trizrK said:**
> Hello, i have a SATA drive for my main hard drive, and a 400 gb HDD with nothing on it. I was wondering how i could use it to save files from Ubuntu onto it.
Thank you in advanceHi, you can setup a separate home partition on it, here are the instructions.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by nzjethro on 2011-07-09
You could also add it to your fstab so that ti automountsd, then create links to the drive from your home partition. This is what I did to enable shared documents, videos, and pictures from an Ubuntu to a Windows install on a separate HDD. The process would be the same for a single Ubuntu install with a separate HDD for files.

---

