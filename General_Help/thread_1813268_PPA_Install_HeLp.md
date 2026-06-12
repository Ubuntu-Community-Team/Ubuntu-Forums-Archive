---
title: "PPA Install HeLp"
date: 2011-07-27
forum: General Help
---

### Post by amr9000 on 2011-07-27
I just want to install the software hosted at this ppa [https://launchpad.net/~c-korn/+archive/ppa](https://launchpad.net/~c-korn/+archive/ppa) through the terminal.. I don't understand what I'm doing wrong but said software 'winepulse' is supposed to have a realistic pulse audio driver and everytime I install 'wine' from the terminal it is 1.2 or whatever it is doesn't work sound wise..
someone please help, I just want to listen to spotify...

---

### Post by oldos2er on 2011-07-27
```
sudo add-apt-repository ppa:c-korn/ppa

sudo apt-get update && sudo apt-get install wine1.3
```

---

