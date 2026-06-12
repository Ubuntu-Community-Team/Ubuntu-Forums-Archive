---
title: "Dropbox not installing and now messing everything else up!"
date: 2012-06-22
forum: General Help
---

### Post by timswait on 2012-06-22
I've been trying to install Dropbox on a Mythbuntu system with a kde desktop (12.04). First off I downloaded and ran the .deb from the website. I then ran the daemon which started downloading files, but got to 99% and then hung. So I tried installing it through the software centre but this also got nearly to the end of the bar and then hung (I left the machine for 30 minutes and the bar hadn't moved) so I had to turn the power off to shut it down. Now whenever I try to do anything involving packages (e.g updates, muon, synaptic, etc) I get an error I assume is from me interrupting it's attempted Dropbox installation, for example Synaptic:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
But when I run "sudo dpkg --configure -a" it immediately tries to install Dropbox, gets to 99% and then hangs again!
Ideally I'd still like to install Dropbox, but as an interim measure I'd at least settle for being able to access package managers, so how can I tell it to forget about trying to install Dropbox for the time being?

---

### Post by howefield on 2012-06-22
Try this thread on the dropbox forum.

[http://forums.dropbox.com/topic.php?id=62952](http://forums.dropbox.com/topic.php?id=62952)

---

### Post by timswait on 2012-06-22
Thanks, I followed that thread through to this one: 
[https://answers.launchpad.net/ubuntu/+source/nautilus-dropbox/+question/201183]("https://answers.launchpad.net/ubuntu/+source/nautilus-dropbox/+question/201183")
Which describes a lot of people having exactly the same problem as me. Unfortunately I can't apply those solutions, as they involve running the apt-get command, which gives the error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
But when I run it it immediately tries to install Dropbox, gets to 99% downloaded and then hangs! so I'm going in circles. It's a bit of a catch 22, I can't run any commands to fix Dropbox because it keeps trying to install. At least with plenty of people reporting the same problem in the last 6 hours, hopefully it'll get fixed and then maybe Dropbox will install and let me run the dpkg configure -a command....

---

### Post by timswait on 2012-06-22
Ah ha,
```
sudo dpkg -r -a
sudo dpkg -P -a
```
Got it to stop keeping to try and install Dropbox!
Now I'll try that workaround...

---

### Post by timswait on 2012-06-22
Right, with the it properly removed, the workaround from [https://answers.launchpad.net/ubuntu/+source/nautilus-dropbox/+question/201183]("https://answers.launchpad.net/ubuntu/+source/nautilus-dropbox/+question/201183") then worked for me!
Cheers for pointing me in right direction Howefield.

---

### Post by Grez on 2012-06-24
Thanks guys. I love you and I want to have your babies!

:guitar:

---

