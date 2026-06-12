---
title: "scaling_min_freq problem"
date: 2006-03-20
forum: General Help
---

### Post by AndreAPL on 2006-03-20
Hi there. I'm using speedstep-centrino (loaded in module), and i'm having some problems. don't understand why anytime i reboot the scaling_min_freq changes to a different value, causing cpu speed to be at 1000 minimum instead of 600mhz... is this normal ?
and when i try to change it via echo:
> 
echo 600000 > scaling_min_freq  
bash: scaling_min_freq: Permission denied
what should i do ??

---

### Post by benvdh on 2006-03-22
Permission denied usually means that you need root access to execute the command. So try using the echo command with sudo :

> sudo echo 600000 > scaling_min_freq

Regards,

Ben

---

### Post by AndreAPL on 2006-04-15
i tryed with sudo and tryed changing file permissions...
now using powernowd with no problems

---

### Post by engla on 2006-04-15
[QUOTE=benvdh]Permission denied usually means that you need root access to execute the command. So try using the echo command with sudo :



Regards,

Ben[/QUOTE]
That doesn't work since only "echo" runs with root permissions while the shell does the actual redirection (and runs as user).
So, rather:
```
echo something | sudo tee /path/to/file
```
tee writes its input to a file, as root in this case

---

### Post by AndreAPL on 2006-04-16
thanks for the great tip :D

---

