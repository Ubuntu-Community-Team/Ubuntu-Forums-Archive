---
title: "How to setup a local ubuntu repository on a removable drive?"
date: 2012-09-14
forum: General Help
---

### Post by Jarretinha on 2012-09-14
Greetings,

I need to build a local ubuntu repository ideally on a removable drive to serve as a transportable mirror. I will use it on some offline clusters. I've already made some progress using debmirror as shown in this community article [https://help.ubuntu.com/community/Debmirror]("https://help.ubuntu.com/community/Debmirror.").

Also, I've went on some troubles with permissions to serve the files with apache2.

Edit.:

After settting the repository and apache, I was able to install new packages using it. But, already installed packages gives this sort of error during install/removal:

```
root@lsdim:/etc/apt# apt-get install libglib2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libasound2: Breaks: libasound2-plugins (< 1.0.24) but 1.0.22-0ubuntu6 is to be installed
E: Broken packages
```

I was unable to update my package list to correct this. 

What am I missing?

---

### Post by dniMretsaM on 2012-09-14
You might want to take a look at [this](http://ubuntuforums.org/showthread.php?t=352460) thread. Not sure if it's exactly what you're looking for, but it might be of some help.

---

### Post by drdos2006 on 2012-09-15
I found it easier to copy all the .deb files from /var/cache/apt/archives/*.deb  to another directory.

regards

---

### Post by Jarretinha on 2012-09-17
Quite useful indeed! I was able to finish my local repository. It's working, But I'm not happy with the overall finish. I'm using a mode 777 on the named partition on the USB HD where the repo is located. I'm not sure which perms/groups to be able to use it on every machine on a per group basis without messing with apache.

---

