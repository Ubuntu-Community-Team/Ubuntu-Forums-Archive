---
title: "compile plib1.8.5"
date: 2009-07-26
forum: General Help
---

### Post by toleolu on 2009-07-26
Having trouble installing a program that is dependent on plib1.8.5. It errors saying that this library is not installed.  Being a total Linux noob, I have no idea what that means.  Could someone explain what I need to do to fix this.  Thanks

---

### Post by SPr on 2009-07-26
Install libplib1.8.5 using Synaptic. Installing programs with Synaptic is easier than compiling from source because Synaptic will resolve any dependency issues.

---

### Post by ajgreeny on 2009-07-26
I note the version in synaptic, ie in the repos is only 1.8.4, so you may be unlucky.  What package do you want to install that needs 1.8.5, and is there a version of it that will work with v1.8.4 which ubuntu can get for you from the repos?

---

### Post by moster on 2009-07-26
Better tell what program you trying to install. It can solve your problem instantly.

---

### Post by toleolu on 2009-07-27
Thanks to all, got it taken care of by removing plib1.8.4c3 (I believe that was the correct file name)  Anyway apt-get remove took care of that file and then plib1.8.5 installed with no problems.    Good learning experience for a Linux noob!!!  Thanks again.

---

