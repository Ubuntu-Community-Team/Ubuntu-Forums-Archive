---
title: "System won't switch off"
date: 2010-05-14
forum: General Help
---

### Post by malel on 2010-05-14
I have just done a clean install of 10.04 and now find that when I come to shut down it will not do so . Even it will not restart after clicking the  restart button. Can someone help me with this please ?

---

### Post by utnubuuser on 2010-05-14
There are a couple threads about not shuting down - I'll see if I can find one for you.
And try this to restart - in a terminal (Applications>>Accessories>>Terminal):
> sudo shutdown -r 0or > sudo shutdown -h nowto shutdown.


1. [http://ubuntuforums.org/showthread.php?t=1469501&highlight=Lucid+shutdown]("http://ubuntuforums.org/showthread.php?t=1469501&highlight=Lucid+shutdown")
2.[http://ubuntuforums.org/showthread.php?t=1305601]("http://ubuntuforums.org/showthread.php?t=1305601")
3.[http://ohioloco.ubuntuforums.org/showthread.php?t=1477052]("http://ohioloco.ubuntuforums.org/showthread.php?t=1477052")

---

### Post by wojox on 2010-05-14
Maybe worth a try. Open your terminal and

```
sudo shutdown -H now
```

---

### Post by wojox on 2010-05-14
Or maybe 

```
sudo poweroff
```

---

