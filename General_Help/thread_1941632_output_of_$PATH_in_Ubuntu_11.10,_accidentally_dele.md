---
title: "output of $PATH in Ubuntu 11.10, accidentally deleted default directories"
date: 2012-03-16
forum: General Help
---

### Post by Vpc on 2012-03-16
Can someone with Ubuntu 11.10 post their output for ```
echo $PATH
``` 
I accidentally deleted all the directories as I was trying to add a directory using the export command in .bashrc i.e. I opened a new terminal window as I was editing before I finished and now $PATH is empty. And I'm worried if I boot from another drive to find the $PATH I won't be able to boot into this drive again.

---

### Post by Vpc on 2012-03-16
> **Vpc said:**
> Can someone with Ubuntu 11.10 post their output for ```
echo $PATH
``` 
I accidentally deleted all the directories as I was trying to add a directory using the export command in .bashrc i.e. I opened a new terminal window as I was editing before I finished and now $PATH is empty. And I'm worried if I boot from another drive to find the $PATH I won't be able to boot into this drive again.

Just checked and saw that PATH is still fine in the other terminal window that was open before the new one. So just fixing the export line in .bashrc by adding `:$PATH` to the end of the export line restored the PATH.

For completeness, the default output of `echo $PATH`
```
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

