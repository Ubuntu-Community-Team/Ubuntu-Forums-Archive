---
title: "Problem with Skype"
date: 2010-11-05
forum: General Help
---

### Post by IL TRIVELLA on 2010-11-05
hey guys I downloaded the version of Ubuntu at 64 bit, and I put in my usb key for try, then now that I'm inside I try to download from [www.skype.com](www.skype.com) the version of skype for Ubuntu [Ubuntu 8.10+ 64-bit]("http://www.skype.com/go/getskype-linux-beta-ubuntu-64") but is not working, when the download is finish and the software center is open, appear to me this:

**Dependency is not satisfiable: ia32-libs (>= 1.6) **

and if I try to download the 32bit version I can't, somebody can help me?

thanks...

---

### Post by Anchovie on 2010-11-05
Go to System -> Administration -> Synaptic Package Manager, once Synaptic is open, click on Settings -> Repositories -> Other Software tab, make sure Canonical Partner repositories are checked, close the Settings window and reload your repository.

Once it's reloaded, go to Search, on the top right corner, and type "skype" with out quotes and look for a package named "skype", not "skysentials" or "skytools", just "skype", right click on that package and left click on "Mark for Installation", it should prompt you to install other required dependencies as well, so just click on "Mark" when the new window pops up. Once you have done that just click on "Apply", it should install Skype and its dependencies.

---

### Post by IL TRIVELLA on 2010-11-05
this is what I see:

[IMG]http://img510.imageshack.us/img510/2245/screenshotxg.png[/IMG]

---

### Post by Anchovie on 2010-11-05
```
sudo nano /etc/apt/sources.list
```

Then add the following lines to your repository...

```
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
```

Once you are done, Ctrl + X, press "y" to save.

```
sudo apt-get update
sudo aptitude install skype
```

See if that works.

---

