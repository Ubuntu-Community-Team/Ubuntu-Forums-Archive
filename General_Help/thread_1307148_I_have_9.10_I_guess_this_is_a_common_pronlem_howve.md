---
title: "I have 9.10 I guess this is a common pronlem howver"
date: 2009-10-30
forum: General Help
---

### Post by vvfrn on 2009-10-30
I have been getting this problem midway through using 9.04 this is my fourth month so about my second month everytime I log on the volume mutes and it is very annoying and cumbersome to be arranging the volume evrytime I need to use the computer! Is there a workaround for this?:KS

---

### Post by andrewabc on 2009-10-31
Did you upgrade from 9.04 or format/install 9.10?
If upgrade it is possible the problem stayed.

---

### Post by Razmear on 2009-10-31
Same issue here that just appeared in 9.10. 
On every restart the volume control starts muted. 
Did not have this issue in 9.04. I did the Upgrade thru Update manager. 
No big annoyance here for me, just verifying the issue for the OP. 

Let me know if you need any system data from my machine to help you resolve the issue.

eb

---

### Post by ikisham on 2009-10-31
I've seen several people with a problem of the sound not keeping its settings after a restart that was solved by uninstalling the alsa-utils package
```
sudo apt-get purge alsa-utils
```

For more issues regarding sound there's this thread too: [http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)

---

