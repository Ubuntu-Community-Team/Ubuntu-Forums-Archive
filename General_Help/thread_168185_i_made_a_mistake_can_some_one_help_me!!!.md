---
title: "i made a mistake can some one help me!!!"
date: 2006-04-30
forum: General Help
---

### Post by H080J03 on 2006-04-30
ok i was messing around with adept and i screwd up the /etc/apt directory, can someone upload theres and let me copy theres?? i didn't make back ups of mine before i started messing with it. (dumb choice by me) but hey you lrean from mistakes

---

### Post by aysiu on 2006-04-30
Go to KMenu > System > Konsole and copy and paste these commands: ```
cd
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo cp breezy.list /etc/apt/sources.list
sudo apt-get update
```

---

