---
title: "Help with screen"
date: 2012-07-10
forum: General Help
---

### Post by josue0098 on 2012-07-10
Hi, I am hosting a minecraft server for my family and friends and I'm using a headless ubuntu 11.10 CLI install. For some time, I've used two aliases to have my server up and running in seconds. I had the following aliases:

alias minecraft='screen -S minecraft'
alias server='java -Xmx1400M -Xms1400M -jar /home/***/minecraft_server.jar nogui'

I have been trying to make it so that I can execute one alias and have both commands run, but all fails. I have tried:

alias server='screen -S minecraft && java -Xmx1400M -Xms1400M -jar /home/***/minecraft_server.jar nogui'

alias server='screen -S minecraft ; java -Xmx1400M -Xms1400M -jar /home/***/minecraft_server.jar nogui'

alias server='java -Xmx1400M -Xms1400M -jar /home/***/minecraft_server.jar nogui > screen -S minecraft'

I'm sorry if some of those are noobish. I am new to command line. Is there any way I could get this to work? What happens is, Screen opens, but the server does not launch. Then, once I either kill screen or detach from it, then the server launches... I don't know what else to do. Thanks in advance :)

---

### Post by josue0098 on 2012-07-10
:edited because the post was deleted:

---

### Post by Toz on 2012-07-10
Try this:
```
screen -S minecraft -m java -Xmx1400M -Xms1400M -jar /home/***/minecraft_server.jar nogui
```

---

### Post by josue0098 on 2012-07-10
WOW! I was way off. Haha. That worked just how I wanted. Could you please explain what exactly -m indicates? I've also been taking this server hosting as a learning experience :)

---

