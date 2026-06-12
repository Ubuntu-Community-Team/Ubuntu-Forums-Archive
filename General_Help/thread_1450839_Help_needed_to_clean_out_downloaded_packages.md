---
title: "Help needed to clean out downloaded packages"
date: 2010-04-09
forum: General Help
---

### Post by MarkProvanP on 2010-04-09
I've just done a system update on my Lucid netbook with an 8GB SSD, and as the downloads totalled 380MB it now reports that there isn't a lot of space left. Before the update, there was more than 600MB space left but not anymore, and I have tried Computer Janitor but it didn't help.

Where can I find all the files that were downloaded when I updated? Is there a way to delete them automatically?

(Lucid netbook remix running desktop UI on a Dell Mini 10v)

---

### Post by Jguy on 2010-04-09
You should be able to use 

```
sudo apt-get clean
```

to clean out package temp files from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/.

---

### Post by colorlessprism on 2010-04-09
you could also look in synaptic and the may be a tab that says something like "residual config" you can remove those and free some space up as well

---

### Post by pastalavista on 2010-04-09
```
sudo apt-get autoclean && sudo apt-get autoremove
```

---

### Post by no2498 on 2010-04-09
restart the computer to clean out the cache files 910 and up
will also help

---

### Post by MarkProvanP on 2010-04-09
Thank you everyone for your help! I'm loving Lucid, btw.

---

