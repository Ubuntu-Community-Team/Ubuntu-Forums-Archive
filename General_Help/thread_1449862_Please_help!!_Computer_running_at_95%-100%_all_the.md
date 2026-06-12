---
title: "Please help!! Computer running at 95%-100% all the time!!!"
date: 2010-04-08
forum: General Help
---

### Post by jeff_flynn on 2010-04-08
Will somebody PLEASE tell me how to make my computer run a little faster (It's constantly at 92%-100%) Here's a screenshot of my System Monitor, Any and all help is very much appreciated.  [ATTACH]152679[/ATTACH]

---

### Post by MooPi on 2010-04-08
Can you show us the processes part of the monitor as well? That way we may be able to determine what is hogging your CPU cycles

---

### Post by jeff_flynn on 2010-04-08
what do i write in terminal to write all the applications that are running?

---

### Post by cgb on 2010-04-08
You could do a screen shot of "top" in terminal to see what is running.   

```
top
```

---

### Post by vzomik on 2010-04-08
> **MooPi said:**
> Can you show us the processes part of the monitor as well? That way we may be able to determine what is hogging your CPU cycles
use the command "top" to find out the reason, and kill it. 
and you can ban it in startup program, or in the path /etc/init.d/THE PROGRAM NAME

---

### Post by jeff_flynn on 2010-04-08
heres top   [ATTACH]152680[/ATTACH]

---

### Post by cgb on 2010-04-08
The only thing running high in your capture is Xorg...  Not showing the 95% to 100% CPU usage on this capture though.  You may want to monitor top for a while and verify what ends up using that amount of processing.  right now Xorg is a little high but not nearly running 95% to 100%..  Need more info.

---

### Post by jeff_flynn on 2010-04-08
cAN I KILL XORG?

---

### Post by cascade9 on 2010-04-08
> **jeff_flynn said:**
> cAN I KILL XORG?

If you want to run without a GUI, yeah, you can kill xorg. 

cgb is right, you only have 22.5% use in the top screensoht. Alos, gnome system monitor can really suck CPU cycles in my expereince.  

BTW, what hardware is that running on?

---

