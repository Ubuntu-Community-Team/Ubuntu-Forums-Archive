---
title: "&quot;Waiting for headers&quot;"
date: 2006-05-03
forum: General Help
---

### Post by 1oki on 2006-05-03
Ok, so when I do an apt-get install/upgrade I sometimes get the "Waiting for headers". It hangs and hangs and hangs, and finally I get fed up and reboot. Sometimes this helps, but other times it doesn’t. I’m assuming it has something to do with the Ubuntu Repository that I am trying to access but, is this on my end or the servers? Also, if I wait long enough... like 10 min, it will finally start to download only to hang again at some point during the download with the same message “Waiting for headers”. Are these headers the same as the headers in emails? 

All this is done after an apt-get update. Its not that it won’t work, I am just curious as to why this happens. Thanks

L

---

### Post by ImmaculateDeception on 2006-05-03
I'm having the same issue. it looks like only the universe and multiverse are affected. Try commenting out the following in /etc/apt/sources.list for now.

# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by 1oki on 2006-05-03
yeah that worked... but I wonder why this was happening...

---

### Post by crazycarlt on 2006-05-03
Same thing happening to me.

---

### Post by Skye on 2006-05-03
I think it's the apt servers in general-  I'm getting the same error, and I'm using Dapper.

---

### Post by MrMojoRising on 2006-05-03
Same problem here:

Using Dapper Beta2



p.s. - It seems that starting up a nother app that uses the network kinda jump-starts the process.....or it could just purley be coinsidence.

---

### Post by yabbadabbadont on 2006-05-03
I had this issue and found many posts flaming the US mirrors.

Following a suggestion in one of the posts, I just removed the "us." from the source lines so that they started with "archive" and haven't had any trouble since.

---

### Post by 1oki on 2006-05-03
[QUOTE=yabbadabbadont]I had this issue and found many posts flaming the US mirrors.[/QUOTE]

Hmm... So it is the repositories... I thought it was somthing to do with my network. also, I didnt know they had a beta out for 6.06. Do now though! Downloading it! :D

---

### Post by MrMojoRising on 2006-05-05
Yup...

Taking away the "us." fixed the problems.

Anyone heard anything official from the repo guys?
Is this getting fixed?

---

