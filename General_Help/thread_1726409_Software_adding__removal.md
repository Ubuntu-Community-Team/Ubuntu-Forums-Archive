---
title: "Software adding / removal"
date: 2011-04-11
forum: General Help
---

### Post by borabora1 on 2011-04-11
[SIZE=3]
I use actually ubuntu on a slow internet connection ( approx200 / 300 kbps ) international, and as I am in China here for local it is hight speed. 

But, I do get some error while on hotmail for example warning "  Script errors " with option window : continue, or close... 

But I tried to add software and it says : impossible to proceed, package software is broken, proceed to repair before adding... 

I want to put a decent photo software as F spot is not really good, for editing. 

Thanks to let me know how i can resole the package software problem, as might come from very low speed and may affect the program? :(

In advance many thanks for your support and feedback! [/SIZE]

---

### Post by spikoley on 2011-04-11
It sounds like there is a broken package.  In order to continue you need to fix it first.  Try the following command.

```
sudo apt-get install -f
```

the slow speed should not effect the program as long as it downloads the whole thing.  It will just take a long time for it to download.

---

### Post by seawolf167 on 2011-04-11
If spikoley's post doesn't work for you, take a look [here]("http://ubuntuforums.org/showthread.php?t=947124"), and follow post #9

---

