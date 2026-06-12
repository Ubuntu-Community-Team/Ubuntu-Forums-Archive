---
title: "How do I update installed apps?"
date: 2009-09-27
forum: General Help
---

### Post by b9k9kiwi on 2009-09-27
I've been using PCs since before they were invented although I am relatively new to Linux (just a couple of years with Ubuntu).

This seems a really stupid question, but how do I update installed applications to a later version?  Firefox does it all for me automagically, but manual updating it is an aspect of Ubuntu which remains opaque to me.

For example, I have an ageing Get-You installed and I would like to install the latest version - but how?  Do I completely uninstall the existing and install the new - or will installing the new locate the existing and update it/overwrite it?

---

### Post by MelDJ on 2009-09-27
if it has a repository, you just have to add it to your source then launch update manager.

---

### Post by Lukios on 2009-09-27
The updates that are default in the repositories are those that ubuntu has deemed safe and stable thus they are always a little behind. Now this doesn't mean that just because Ubuntu doesn't approve the newer version that it is crap, often times it just simply means they haven't had a chance to test it, or that it has a few minor issues with certain computers and they are being picky about it. Either way, its your choice. Go the the developers website and find their download section. Often times they will have a section for Ubuntu or Debian. Go to that section and look for a repository like this 

```
deb [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu) jaunty main 
```

Some times they will only include the "deb http:// " which is fine. Just simply add it to your /etc/apt/sources.list. You will have to be root. You can do this either by terminal 

```
Sudo gedit /etc/apt/sources.list
```

or go the the apt folder and right click on the window and choose open as root then open the file sources.list. The repositories are available for those who want automatic updates, if you don't mind updating the program your self, as you feel you need to, then you can just look for the .deb file and download and install through gdebi package installer. If you would like to keep it updated and you can find the repositories at their website, you can often times find them at [https://launchpad.net/](https://launchpad.net/) just search for their program and your distro or version of the distro and you should be able to find it.

These directions should work for most Debian or Ubuntu based Distros, but if you need any further help, just let me know.

---

### Post by b9k9kiwi on 2009-09-28
Thanks for the help - I had a suspicion that the process would be reasonably friendly.

---

