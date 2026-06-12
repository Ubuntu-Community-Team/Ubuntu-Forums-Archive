---
title: "User account messed up, file owner doesn't exist - how to fix?"
date: 2011-04-26
forum: General Help
---

### Post by Mar10e on 2011-04-26
Hi all,

On my Ubuntu 10.10 laptop something went very, very wrong. Not sure exactly what was done - wasn't there - but somehow I am no longer file owner on the system and my desktop has changed. The fileowner is now a tempaccount my 'computer helper' created and used ...

I can't figure out what he did (I gave him te laptop to fix some Java-issues, I'm a Linux/Ubunto n00b) exactly and he's not helping so I guess it's time for me to learn myself - which I should have done in the first place ...

What I know:
- there's now 2 users, my account (1000) and a newly created one (1001)
- my original desktop is gone and fileowner is the new account, not me
- firefox still has all settings, bookmarks etc. (which I can use but not change/edit), thunderbird can't start (needs a profile name and then find folder unwritable)

What I need/want:
- My email back! :)
- Want to be owner of my files again

Thank you for any help!

---

### Post by Mar10e on 2011-04-26
Sorry for the quick reply -- I'm planning a complete re-install later tonight. If there's a way to avoid that I'd be very happy, so any help you may be able to give is much appreciated.

---

### Post by btindie on 2011-04-26
If you're still able to log into your system then you can change the owner of your files. If you can't then you can still do it by using a LiveCD.

From a terminal type the following
```
sudo chown -hR 1000:1000 /path/to/home/directory
```If you're running the command from your proper system then the path would more than likely be /home/<username>. If it's from a LiveCD then it's probably something like /media/<partition_name>/home/<username>. That command will change the owner of the files by performing the operation as root allowing you to access them once again.

---

### Post by Mar10e on 2011-04-26
Thank you!

I got an error, but it worked! 
Now I can get to work on the desktop, no need to re-install.

Again, thank you very much!

---

### Post by btindie on 2011-04-26
Cool, please mark your thread as solved for others by editing the subject.

---

