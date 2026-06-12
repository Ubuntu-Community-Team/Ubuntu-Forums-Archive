---
title: "ubuntu root partition full?"
date: 2010-11-17
forum: General Help
---

### Post by RastaManPower on 2010-11-17
hello guys i have been getting a message saying that my root partition is almost full.. how is it possibile? my home directory is on a separate partition with 150gb free and my root partition 18gb
how is it possible that it is alredy full? i dont have many programs installed
[http://img200.imageshack.us/img200/7236/screenshotixz.png](http://img200.imageshack.us/img200/7236/screenshotixz.png)

---

### Post by kleskjr on 2010-11-17
wow, you could delete all old packages and kernels manually, but it will be easier if you install ubuntu-tweak and do it from there.

---

### Post by RastaManPower on 2010-11-17
i have notused that in folder   /var/log is used 13 gb  can i delete all that?
[IMG]http://img593.imageshack.us/img593/5752/screenshot1zl.png[/IMG]
[IMG]http://img809.imageshack.us/img809/7937/screenshot2vh.png[/IMG]

---

### Post by kleskjr on 2010-11-17
huge log files means that probably there is something wrong in your system, take a look on them.

You van delete the logs manually or using bleachbit. I would recommend you to have a look at them first.

---

### Post by trundlenut on 2010-11-17
It could be some log file has gone mad and eaten all the space.  I would use the disk usage analyser, It's under Applications->Accessories and scan root partition.

Oops too long between hitting reply and post there!

---

### Post by lobralleo on 2010-11-17
You can start by cleaning up the packages of downloaded updates: you can do this either by removing manually all .deb files in /var/cache/apt/archive/ or simply by running in terminal:

```
sudo apt-get clean
```

Hope this helps!

---

### Post by RastaManPower on 2010-11-17
i added one pic.. can i delete all the log directory?

---

### Post by WorMzy on 2010-11-17
My /var/log folder is 13*MB*. Judging from your kernel log, I'd say that you probably have a serious problem somewhere, and it's been trying to get your attention for a good long while.

---

### Post by trundlenut on 2010-11-17
> **RastaManPower said:**
> i added one pic.. can i delete all the log directory?

I wouldn't delete the directory and I would definately check through the messages and kern.log to find out what's going on, something does not seem to be happy.

---

