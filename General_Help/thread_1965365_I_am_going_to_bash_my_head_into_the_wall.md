---
title: "I am going to *bash* my head into the wall"
date: 2012-04-25
forum: General Help
---

### Post by clj3 on 2012-04-25
__](*,)
I am trying to make a vanilla server for minecraft and bash wont let me run the server!!! I also have a bukkit server and it runs fine, I had to create the .sh file to run the bukkit server and the vanilla server (not at same time, I am not stupid)  but the vanilla server wont run?!?
here is the bukkit servers .sh file:
""cd ~/Desktop/Minecraft
java -Xincgc -Xmx1024M -jar craftbukkit.jar nogui""

here is the vanilla servers .sh file:
""cd ~/minecraft
java -Xincgc -Xmx1024M -jar minecraft_server.jar nogui""

I used the chmod -x command on both files and in same place. it will run the bukkit but not the other please help!!??!!
](*,)

---

### Post by CharlesA on 2012-04-25
What error are you getting?

It would be a better idea to use the full path instead of cd'ing into the directory.

```
java -Xincgc -Xmx1024M -jar ~/Desktop/Minecraftcraftbukkit.jar nogui
```

```
java -Xincgc -Xmx1024M -jar ~/minecraft/minecraft_server.jar nogui
```

---

### Post by clj3 on 2012-04-25
bash: ./starts.sh: Permission denied
starts.sh is for vanilla server

---

### Post by Vaphell on 2012-04-25
chmod +x not -x
-x unsets the executable bit, not sets it

---

### Post by clj3 on 2012-04-25
](*,) I cant believe i did not notice that!!!!!!
Thank you a lot for this help

---

