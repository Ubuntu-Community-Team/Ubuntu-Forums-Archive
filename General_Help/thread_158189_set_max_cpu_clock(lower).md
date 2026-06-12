---
title: "set max cpu clock(lower)?"
date: 2006-04-10
forum: General Help
---

### Post by mistamcgoo on 2006-04-10
I have an acer aspire 1300 laptop, with a 1400 athlon xp cpu(i think mobile). Due to bad cooling design, it can run up to more than 70°c when under load a while. 
i have a cpu and temp monitor installed on the panel, when it isn't doing much, 
the cpu clock lowers to 500mhz and temps go to 40-50°, sometimes even lower, 

Is there any application or command that can lock the max speed to 800 mhz for example (for when the pc is under load a longer time) and change it back to "default"setting when i'm done? Is it safe for the hardware? 

i noticed in the klaptop program in panel that i can change "performance profile"
is currently set to "userspace" but it doesn't seem to make difference when i set it 
to other modes (conservative, powersave, ..)

ps, this is a bit far fetched , but is there any way to take over control of the internal fan? 
it starts to cool far too late(one of the problems with this model). or would this be impossible?

---

### Post by GoldBuggie on 2006-04-11
about the fan control.

There is possibility of controling the fan. Unfortunately there might be vendor specific things or not. Since I have a toshiba I use the toshset command but some things that you can try or look into are:
1) modprobe fan - the fan command

2) echo -n "0" > /proc/acpi/fan/state

---

### Post by mistamcgoo on 2006-04-11
i just tried those commands
when i do sudo modprobe fan it goes back to prompt after i press "return"

when i give the second command i get this
root@aspire:/proc/acpi/fan# echo -n "0" > /proc/acpi/fan/state
bash: /proc/acpi/fan/state: No such file or directory

i checked the directory, the /proc/acpi/fan/ folder exists, but this is empty, 
the /state folder is not in it.

---

