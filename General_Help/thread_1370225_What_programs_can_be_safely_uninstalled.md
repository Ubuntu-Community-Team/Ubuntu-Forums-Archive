---
title: "What programs can be safely uninstalled?"
date: 2010-01-02
forum: General Help
---

### Post by Ero on 2010-01-02
What programs can be safely removed to free up space? I'm working with a 4GB SSD (actually 3.3GB) and Ubuntu itselfs takes 2.2GB and after updating it I only have 500MB left. I want to remove everything that can be removed (things like games and such).

Thanks

---

### Post by MelDJ on 2010-01-02
install a lighter DE. openbox or lxde for instance

---

### Post by HappyFeet on 2010-01-02
Go for it. Just remember to do
```
sudo apt-get clean && sudo apt-get autoremove
```
when you are done.

---

### Post by jonest1 on 2010-01-02
On a small netbook, you may want to get rid of large applications like OpenOffice and the Gimp, unless you really need them.  Those two should be a couple hundred MBs.

Also, check if you have language packages installed which you do not need.  

The games are not that big, but I believe you can uninstall.

The suggestions by HappyFeet are good for regular maintenance as updates are placed in cache on your disk, etc.

---

### Post by HiImTye on 2010-01-02
> **jonest1 said:**
> The suggestions by HappyFeet are good for regular maintenance as updates are placed in cache on your disk, etc.
and autoremove removes no longer used libraries

---

### Post by Ero on 2010-01-02
I have tried the autoremove and removing orphaned files but there's nothing much to remove. I dont really need GIMP but I definetely need Open Office (at least Word, Excel and Powerpoint)for school work. 

I am very new to linux and know almost nothing so I'll need a really easy and neat DE like Ubuntu to learn from. If you have any suggestion they are very welcomed. 

Thanks for the help.

---

### Post by Muscovy on 2010-01-02
Evolution can free up some space if you don't use a mail client. And you can remove individual openoffice programs that you don't need.

---

### Post by ron999 on 2010-01-02
Hi
localepurge will strip out all the foreign languages.
Just set it up to keep the language you use.
```
sudo apt-get install localepurge
```

logrotate will automatically remove old logs.
```
sudo apt-get install logrotate
```

---

