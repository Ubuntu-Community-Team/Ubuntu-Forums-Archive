---
title: "Novice user having problems with sources.list"
date: 2009-08-20
forum: General Help
---

### Post by duckdown on 2009-08-20
Hi everyone

I am a novice user, but just bought a VPS server and it came with Ubuntu 64bit.

Unfortunately, I think the /etc/apt/sources.list it shipped with is badly out of date and/or broken..  Any time I try to apt-get ANYTHING, it spits out tons and tons of 404 errors and refuses to install anything.

I have made a pastebin of the sources.list , and some example output I'd get when I'd try an apt-get command

Hopefully this isn't too difficult to fix, any help would be greatly appreciated as soon as possible so I can start using this sytem I paid for!

Thanks in advance

Here is the pastebin:

[http://bcas.tv/paste/results/rETuLP27.html](http://bcas.tv/paste/results/rETuLP27.html)


cheers!!!

---

### Post by michy99 on 2009-08-20
Probably the server is down temporarily. You can either wait and try again later, or switch to a different server. I don't know if you have the Gnome desktop installed, but if you do, go to System -> Administration -> Software Sources and change the server where it says 'Download from.' If you don't have a desktop installed, I guess you would have to edit sources.list by hand to use a different server. I would suggest trying us.archive.ubuntu.com.

---

### Post by spcwingo on 2009-08-20
You can try changing your repo mirror in synaptic if you don't want to wait for the main server to come back online.

---

### Post by epsolon77 on 2009-08-20
I am fairly novice as well, but looking through my output after running an sudo apt-get update I get no errors, and my list is only about half as long.  I noticed several duplicates in the file posted.  Also, just to bring this down to the most basic level so we don't miss anything stupid, make sure you computer can ping the internet and make sure you are running the apt-get as root
```
sudo apt-get update
```

---

