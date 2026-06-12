---
title: "Can't Install Ubuntu 12.04"
date: 2012-08-31
forum: General Help
---

### Post by alwayscarmen on 2012-08-31
I'm trying to install Ubuntu 12.04 into a virtual machine and getting the error "this kernel requires the following features not present on the cpu: pae"

Kind of surprised since the PC I'm using is only about 2 years old, but anyways, I read that you can install an older version and then upgrade to 12.04.

My question is where can I get an older version of Ubuntu.  When I go to the download page ( [http://www.ubuntu.com/download](http://www.ubuntu.com/download) ), the only version offered is Ubuntu 12.04.

Thank you

---

### Post by dgharmon on 2012-08-31
> **alwayscarmen said:**
> I'm trying to install Ubuntu 12.04 into a virtual machine and getting the error "this kernel requires the following features not present on the cpu: pae"

I've no idea about virtual machines, but PAE is what allows 32 bit Linux to address more than 4GB of memory, so maybe there is a configuration option in your VM for this ...
--

[Enabling PAE]("https://help.ubuntu.com/community/EnablingPAE")

---

