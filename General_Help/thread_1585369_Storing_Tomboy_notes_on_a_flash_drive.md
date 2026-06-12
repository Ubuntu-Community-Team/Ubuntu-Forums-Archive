---
title: "Storing Tomboy notes on a flash drive"
date: 2010-09-30
forum: General Help
---

### Post by JohnElway on 2010-09-30
I often work on two different computers, so I'd like to keep my Tomboy notes on a flash drive so I can easily view and modify my notes from either computer. Rather than setting up some kind of messy synchronization scheme between the flash drive and the tomboy folders on both computers, I'd rather just have Tomboy directly load the notes from my flash drive.

I found this post which seemed to give me all the info I needed: [http://ubuntuforums.org/showthread.php?t=1427954](http://ubuntuforums.org/showthread.php?t=1427954). I deleted everything in my ~/.local/share/tomboy folder (and moved it to /media/flashdrivename/tomboy) and inserted the following code in my ~/.bash_aliases file to change the TOMBOY_PATH:

```
if [ -d "/media/flashdrive" ] ; then
    TOMBOY_PATH="/media/flashdrive/tomboy/"
fi
```

However, when I restarted my computer it showed that I have no notes. Any ideas on what I'm doing wrong?

---

