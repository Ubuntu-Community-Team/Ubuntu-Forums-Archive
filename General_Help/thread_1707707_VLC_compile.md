---
title: "VLC compile"
date: 2011-03-15
forum: General Help
---

### Post by hsincredible on 2011-03-15
I successfully cloned the vlc git-repo on my hd and also compiled and installed it on my system...
but as I closed the terminal, all the work went in vain as the downloaded vlc git-repo folder disappeared ... :(:(
Why did this happen and how do i keep the code and install vlc permanently ?

---

### Post by 3Miro on 2011-03-15
> **hsincredible said:**
> I successfully cloned the vlc git-repo on my hd and also compiled and installed it on my system...
but as I closed the terminal, all the work went in vain as the downloaded vlc git-repo folder disappeared ... :(:(
Why did this happen and how do i keep the code and install vlc permanently ?

There is no reason for a git folder to disappear. Can you post the exact commands that you used.

---

### Post by hsincredible on 2011-03-15
> **3Miro said:**
> There is no reason for a git folder to disappear. Can you post the exact commands that you used.

I ran the following commands after getting the git-repo :
```
git log
gitk
```

gitk was not present on system then I ran ```
sudo apt-get install gitk
```
although no other download manager was opened, terminal displayed ```
Could not get lock /var/lib/dpkg/lock ubuntu
```
so i removed apt-get manually from processes and restarted the terminal...thats when i found that the folder was no more...

---

### Post by 3Miro on 2011-03-15
> **hsincredible said:**
> 
so i removed apt-get manually from processes 

Why did you do that? Had you called apt-get before that? Which process started the other instance of apt-get?

Where was the folder in the first place?

---

### Post by hsincredible on 2011-03-15
> **3Miro said:**
> Why did you do that? Had you called apt-get before that? Which process started the other instance of apt-get?

Where was the folder in the first place?

I am not sure which process started it...
The folder was in my home folder.

---

### Post by 3Miro on 2011-03-15
This makes no sense. Did you get errors of the sort "not enough space" or something like that. Is your HDD full by any chance?

It is possible that the folder was just cached and when you killed a process, it never actually got written to the HDD. However, if you have managed to successfully compile and install VLC, then this shouldn't happen.

I am getting out of ideas on what can possibly go wrong.

---

### Post by andrew.46 on 2011-03-16
> **hsincredible said:**
> how do i keep the code and install vlc permanently ?

There is a guide on these forums that deals in some detail with compiling and installing vlc-git, perhaps you might find a few tips there?

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

Andrew

---

### Post by hsincredible on 2011-03-16
> **3Miro said:**
> This makes no sense. Did you get errors of the sort "not enough space" or something like that. Is your HDD full by any chance?

It is possible that the folder was just cached and when you killed a process, it never actually got written to the HDD. However, if you have managed to successfully compile and install VLC, then this shouldn't happen.

I am getting out of ideas on what can possibly go wrong.

Thanx a lot for ur help...I too have no idea what happened...I re-cloned the git repo and now everything works fine.:)

---

