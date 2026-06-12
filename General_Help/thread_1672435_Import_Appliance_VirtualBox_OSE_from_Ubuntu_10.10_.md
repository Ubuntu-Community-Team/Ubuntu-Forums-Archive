---
title: "Import Appliance VirtualBox OSE from Ubuntu 10.10 to Ubuntu 11.10"
date: 2011-01-20
forum: General Help
---

### Post by Fredhoud on 2011-01-20
:confused:I’d like to know if I can import my VirtualBox OSE from Ubuntu 10.10 to Ubuntu 11.10 coming up in April?  I will hold off and wait until April, before purchasing my new computer, if I have to build the VirtualBox OSE from scratch, as I have spent a lot of time on it.  Does any one know if that’s going to work on the version 11.10, coming up in April?

Thanks,
Fredhoud

---

### Post by Vaphell on 2011-01-20
you ask if your customized virtual guest systems will work? Virtualbox itself is just a click to select, apply in the package manager so i think you talk about virtual machines. If so then most likely they will work - you'd need to copy hidden .VirtualBox folder where the virtual systems are stored to your new computer.

---

### Post by Azdour on 2011-01-21
Hi,

The one thing I'd like to suggest is to try and keep the same version of VirtualBox that you have currently in 10.10 when you install/upgrade to 11.10. I am not sure what version of VirtualBox will be available in 11.10 - hopefully the same one you are using now.

I recently upgraded from 8.04 - 10.04 (which is quite a large jump) and found that in 10.04 there was a new version of VirtualBox that had slight differences in its files. In the end I had to manually edit the various xml files to get it to work.

---

