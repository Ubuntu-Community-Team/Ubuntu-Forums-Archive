---
title: "why is bmpanel2 not in the repos?"
date: 2011-03-31
forum: General Help
---

### Post by TheDexter1111 on 2011-03-31
so I recently reinstalled lucid 10.04 and sudo apt-get install bmpanel2 doesn't work... either does pypanel or tint2.. I could find tint2 in synaptic package manager, but not bmpanel2 or pypanel 

I understand i could go to the website and download the tar.gz but im lazy, and im also just curious as to why its not working anymore...
any ideas?

---

### Post by zvacet on 2011-03-31
It looks that packages are not in repos any more.

---

### Post by Krytarik on 2011-03-31
Hi, you could install it through this PPA:
[https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp)

To do so, just run these commands:
```
sudo add-apt-repository ppa:alex-p/notesalexp
sudo apt-get update
sudo apt-get install bmpanel2
```
Greetings.

---

### Post by TheDexter1111 on 2011-04-01
awesome! will do! if only he has onmenu in there too.. know where i can get that one from?

---

### Post by Krytarik on 2011-04-01
> **TheDexter1111 said:**
> if only he has onmenu in there too.. know where i can get that one from?
I really don't know this app. I only looked up the PPA once for another member, who was trying to compile it on his own.

---

### Post by vbmds on 2013-01-21
Unfortunately Krytarik's console instructions no longer work, bmpanel2 not found.

---

### Post by overdrank on 2013-01-21
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

