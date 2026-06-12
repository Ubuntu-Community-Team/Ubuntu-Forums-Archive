---
title: "Limited Local Repository"
date: 2010-09-28
forum: General Help
---

### Post by btrichardson on 2010-09-28
Hello All,

I have an Ubuntu 10.04 Desktop machine that cannot be connected to a network. I'm needing to install some new packages on it in support of a new development environment, and rather than generating and creating the 9 DVDs required to hold main, restricted and universe, I was wondering if there's any way to create a limited local repository that only has the required software libraries and their dependencies in it. The limited local repository would still have the same layout as a normal Ubuntu repository, but only have the files necessary in support of a smaller size.

I can use apt-rdepends to find out what all the dependencies of the libraries are, I just don't know if there's a way to use the output of apt-rdepends in some way to create a limited local repository.

Please help!

--
Bryan

---

### Post by ankspo71 on 2010-09-28
Hi,
You can try these:

[http://keryxproject.org/](http://keryxproject.org/) 
(for use in Windows, Mac, and Linux)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) 
(for Linux only, and available in Ubuntu's repositories)

Those programs allow you to create mini personal repositories (after you install those programs on another computer with Internet, of course). If you plan to your live cd to install these programs onto, make sure you bring a USB storage stick with you to transfer files onto, (or an extra cd if the other computer has dual drives :P).

---

### Post by btrichardson on 2010-09-29
Thanks for the response! I'll definitely check out AptOnCD, as it looks very promising.

As an aside, I did end up figuring out a way to do this via a combination of debmirror, apt-rdepends and debpartial. I bet AptOnCD would have made it much easier though! :)

--
Thanks again!
Bryan

---

