---
title: "question"
date: 2011-03-05
forum: General Help
---

### Post by darkian22 on 2011-03-05
whenever i try to download or install wine it says : Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
any help ?

---

### Post by minigeek on 2011-03-05
> **darkian22 said:**
> whenever i try to download or install wine it says : Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
any help ?

Hi

Check to see if apt-get is already running.

In a terminal run the following command.

```
ps -ef | grep apt-get
```

---

### Post by vivek.pandey on 2011-03-05
i guess you are installing wine from both terminal as well as synaptic or running two processes that need your password simultaneously,,,end the other process

---

