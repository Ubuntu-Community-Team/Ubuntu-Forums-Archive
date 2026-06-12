---
title: "How to restart HAL in Ubuntu 10.04"
date: 2010-11-15
forum: General Help
---

### Post by Alcareru on 2010-11-15
Hi
I have a simple question that started bugging the crap out of me: How do I restart HAL service in ubuntu 10.04. AFAIK on some systems you would do something like this:
sudo /etc/init.d/haldaemon restart
or something like
sudo service hald restart

With Ubuntu however there is no haldaemon, hal, hald or anything like that in anywhere in /etc/*.d/. Hal is also not listed among:
service --status-all

man hald contains nothing useful. Is the only way to do this to just kill it and then start it with hald --deamon=yes or something? (sudo needed I guess?)

---

### Post by Alcareru on 2010-11-16
Hmm.. weird. I suppose this is some what difficult because HAL it is more or less deprecated on Ubuntu 10.04. On my laptop HAL isn't running though it's still installed. I wonder why I have it running on my desktop?

---

### Post by dino99 on 2010-11-16
[https://answers.launchpad.net/ubuntu/+source/hal/+question/98081](https://answers.launchpad.net/ubuntu/+source/hal/+question/98081)

---

### Post by linux-hack on 2010-11-16
Well you could try installing it !!!

---

### Post by Alcareru on 2010-11-29
> **linux-hack said:**
> Well you could try installing it !!!

Well as I said it was already running so I'm pretty sure it was installed too :). Well this all don't matter anymore as my one of my HDDs died and I lost all my previous Ubuntu installations. I'm now running all new ubuntu 10.10 and there's no more hal daemons to bug me.

---

