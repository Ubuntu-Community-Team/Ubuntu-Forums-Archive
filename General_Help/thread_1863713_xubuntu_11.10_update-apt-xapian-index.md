---
title: "xubuntu 11.10 update-apt-xapian-index"
date: 2011-10-18
forum: General Help
---

### Post by oldgreygary on 2011-10-18
Since upgrading to Xubuntu 11.10 a process called update-apt-xapian-index has been running which seems to be utilising 100% cpu and making it impossible to use my pc. The process is kicking off every day. I do power off and on, on a daily basis. Two questions. Can anyone explain what this process is? Second question does it have to run daily and is there a need for it to run or can it be done an alternative way?

Thanks

Gary

---

### Post by gsmanners on 2011-10-18
If you use Synaptic, Software Center, Adept, or Aptitude you will need that. It primarily builds an index of package tags for those applications.

See: [http://www.enricozini.org/sw/apt-xapian-index/](http://www.enricozini.org/sw/apt-xapian-index/)

---

### Post by oldgreygary on 2011-10-22
I still have the problem that this process is taking at least 1 hour and making it impossible to use my PC. Is there a way of stopping it running automatically and setting it running at a time that would be more suitable?
As it is becoming very frustrating as a short process of checking emails/websites is becoming a chore when this process starts.

So perhaps someone could explain how and where it is started from and how that can be changed?


Thanks

Gary

---

### Post by gsmanners on 2011-10-22
I think it gets run from /etc/cron.weekly/apt-xapian-index, so if you can modify that the way you want...

---

