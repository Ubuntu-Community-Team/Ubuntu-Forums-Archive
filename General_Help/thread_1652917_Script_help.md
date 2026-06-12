---
title: "Script help"
date: 2010-12-25
forum: General Help
---

### Post by hantechbl on 2010-12-25
I want to make a script that specifies how much ram to launch minecraft server with, so far I have:
```
read $ra
java -Xmx$raM -Xms$raM -jar minecraft_server.jar nogui
```
but I knowthat that won't work because there is the M at the end of the variable $ra, is there a way I could make this work?  I believe that the M at the end is required to specify the measurement unit.

---

### Post by sisco311 on 2010-12-26
Try:
```
read ra
java -Xmx${ra}M -Xms$raM -jar minecraft_server.jar nogui
```

[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

---

