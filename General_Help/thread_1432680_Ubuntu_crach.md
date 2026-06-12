---
title: "Ubuntu crach"
date: 2010-03-18
forum: General Help
---

### Post by adeelm on 2010-03-18
hi,
     I was using ubuntu 9.10 and I updated it today using the apt-get update and apt-get upgrade commands.

after that my machine started to halt. I had to forcefully shut down the machine couple of times. 
then it did not even showed me the login screen. the machines boot up  but does not shows the login screen. I tried to reinstall using the CD but it does not reinstall. It asks me which language will you use to install. I say English, then it starts to load and takes a lot of time then it just halts again. I tried to also install ubuntu 9.04 and MS windows XP. but all failed to install.

Please advise what should I do?

Thanks
Adeel

---

### Post by zvacet on 2010-03-18
Maybe you can not login in graphical mode because of upgrade (I think it was new kernel update).Boot in recovery mode and type

```
dpkg --configure -a
apt-get -f install
```

after that back to normal boot and if you then get to CLI type

```
startx
```

Not being able to reinstall shouldn't be related with your previous problem.

---

### Post by adeelm on 2010-03-19
Thank you zvacet,
                            The issue was not with ubuntu. my hardware team told me after the inspection that mother board was faulty. they have fixed it now. and I am using the same ubuntu. 

Thanks
Adeel.

---

