---
title: "Screen won't start from script"
date: 2011-07-21
forum: General Help
---

### Post by Rikeshar on 2011-07-21
Hello all, maybe you can help me figure something out.

I've got screen installed, and I have a script which I"m trying to use to start a screen session:

```
# Path to .jar
PATH=/usr/games/Minecraft

cd $PATH
screen -S minecraft java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui
```

When I run this though, in the terminal I get the error:

[HTML]/usr/games/Minecraft/start.sh: line 5: screen: command not found[/HTML]

Why would it be telling me this? If I run the command manually everything starts fine.

---

### Post by Habitual on 2011-07-21
```
PATH=$PATH:/usr/games/Minecraft
```

---

### Post by Rikeshar on 2011-07-21
Awesome, that worked! 

Would you mind explaining what that extra $PATH: in there does?

---

