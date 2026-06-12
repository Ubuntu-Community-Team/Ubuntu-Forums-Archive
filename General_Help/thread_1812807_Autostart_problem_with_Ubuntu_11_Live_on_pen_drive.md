---
title: "Autostart problem with Ubuntu 11 Live on pen drive, please help me..."
date: 2011-07-26
forum: General Help
---

### Post by brunoshady on 2011-07-26
ok guys, help me out here with the autostart problem..

I have 5 scripts that need to be executed on the system boot.


start.sh:
```


#!/bin/bash
sleep 20
gnome-terminal --title gpu.overclock --command "sh /home/corelinux1/gpu.overclock.sh"
gnome-terminal --title gpu0.miner --geometry=+0+0 --command "sh /home/corelinux1/gpu0.miner.sh"
gnome-terminal --title gpu1.miner --geometry=-0+0 --command "sh /home/corelinux1/gpu1.miner.sh"
gnome-terminal --title gpu0.fan --geometry=+0-0 --command "sh /home/corelinux1/gpu0.fan.sh"
gnome-terminal --title gpu1.fan --geometry=-0-0 --command "sh /home/corelinux1/gpu1.fan.sh"

```


so this start.sh, when executed from the terminal, as "sh /home/corelinux1/start.sh", everything goes fine, all 5 scripts are executed, the miners starts fine, the fans to, etc etc, except to the fact that the terminal where I executed didn't close itself (I want that)


so I added the command "sh /home/corelinux1/start.sh" at the Startup Applications on System Settings (Ubuntu 11), but when the system goes up, every command from the script (execute the others scripts) is executed only if the previous script is closed, AND the miner scripts gives errors of pypopencl include (don't know why)...

the gpu.overclock.sh is executed, and then, the gpu0.miner.sh is only executed when the gpu.overlock.sh closes itself.. so the gpu0.miner.sh is executed and gives the include error, so, it closes itself too, making the gpu1.miner.sh execute and giving the same error... then when it closes, the gpu0.fan.sh is executed, but it don't give any errors, so it stays running and the gpu1.fan.sh is not executed at all, or only if I close the gpu0.fan terminal...


what a **** should I do? this is making me crazy!!!

and sorry if it couldn't be more specific, but please help me out here...



ps:
oh, and I did another script called autostart.sh, with "sh /home/corelinux1/start.sh" on it, and replaced with the start.sh command on the Startup Applications, but it happens the same thing...

---

### Post by galvatron408 on 2011-07-26
maybe you should put & at the end of your line; that way, the process will be pushed in to the background

---

### Post by brunoshady on 2011-07-26
you mean 

```


#!/bin/bash
sleep 20
gnome-terminal --title gpu.overclock --command "sh /home/corelinux1/gpu.overclock.sh &"
gnome-terminal --title gpu0.miner --geometry=+0+0 --command "sh /home/corelinux1/gpu0.miner.sh &"
gnome-terminal --title gpu1.miner --geometry=-0+0 --command "sh /home/corelinux1/gpu1.miner.sh &"
gnome-terminal --title gpu0.fan --geometry=+0-0 --command "sh /home/corelinux1/gpu0.fan.sh &"
gnome-terminal --title gpu1.fan --geometry=-0-0 --command "sh /home/corelinux1/gpu1.fan.sh &"


```

?


if yes, I will give it a try, but the first script doesn't need to be running on background... is just a command, but I will try it out

---

### Post by brunoshady on 2011-07-27
didn't work with the &... same thing

---

### Post by brunoshady on 2011-07-27
bump

---

### Post by brunoshady on 2011-07-28
nobody? =(

---

