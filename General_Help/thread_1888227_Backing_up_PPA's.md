---
title: "Backing up PPA's"
date: 2011-11-28
forum: General Help
---

### Post by futralistic on 2011-11-28
This may be a crazy question, but is there a way to back up your PPA's in ubuntu?

I have a fair amount of ppa's that I have added over time, most of them I do not remember and some of them I completely forgot that I added at all. 

If in the future I do a new install on the same machine or a new one, is there any way to "expot" and "import" my current ppa's?

Thank you.

---

### Post by Frogs Hair on 2011-11-28
PPAS are usually made with one version of ubuntu in mind and if the developer chooses to update for the next version you can keep using them .

The package dependencies may change for a newer version of Ubuntu so it is best reinstall them if they are still active . If upgrading it is best to disable PPAS to avoid possible compatibility problems .

Always check  PPA compatibility before adding them to a new installation . By looking in software sources you can identify your installed PPAS .

The developer of a PPA may loose interest or no longer need the PPA due improvements in other software and they simply become obsolete .

---

### Post by Alwimo on 2011-11-28
What I've done is look at the PPA names in Software Sources and create a text file that I can just copy/paste into the terminal to set them all up again.
 
It's just, for example, "sudo add-apt-repository ppa:tiheum/equinox"

---

### Post by batharoy on 2011-11-28
[http://askubuntu.com/questions/24022/how-can-i-backup-my-repositories]("http://askubuntu.com/questions/24022/how-can-i-backup-my-repositories")

> Many people find it easier to handle backing up and restoring a single file rather than dealing with a directory of files (as the other mentioned solutions require). If you are like this, and you do not care about having each PPA stored in its own file inside of /etc/apt/sources.list.d/, you can use the following command to store all of your added repositories in a single file called sources.list located in your home directory.

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/* > ~/sources.list
```

You could then move this file to /etc/apt/sources.list and do sudo apt-get update to re-add the repositories. If you are planning to use this backup on another computer, make sure that the version of Ubuntu on the machine matches the versions in the sources.list file, otherwise, you might have some problems.


---

