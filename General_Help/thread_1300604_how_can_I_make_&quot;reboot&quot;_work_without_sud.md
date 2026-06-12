---
title: "how can I make &quot;reboot&quot; work without sudo."
date: 2009-10-25
forum: General Help
---

### Post by Renée Jade on 2009-10-25
Hey all,

I use Ubuntu on my personal laptop and it really has nothing very important on it. So I would love to be able to change the access permissions on some commands so that I can execute them without sudo. I don't want to get rid of sudo completely though, it has saved me from some near disasters. So, using "poweroff" and "reboot" as examples, how can I make it so that I can execute them as renee instead of root?

Thanks heaps :D

---

### Post by nikhilbhardwaj on 2009-10-25
you can do it with hal
i'll post the details in a couple of mins

---

### Post by nikhilbhardwaj on 2009-10-25
ok
here are the links
[http://forums.debian.net/viewtopic.php?t=35396](http://forums.debian.net/viewtopic.php?t=35396)
and
[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)

hopefully that's what you were looking for

---

### Post by Penguin Guy on 2009-10-25
Run [COLOR="Green"]sudo visudo[/COLOR], press [COLOR="Green"]i[/COLOR], then add the following onto the end of the list:
```
ALL     ALL=NOPASSWD: /sbin/shutdown
```
Now type [COLOR="Green"]sudo shutdown now[/COLOR] and it will shutdown without asking for a password.

---

### Post by 3rdalbum on 2009-10-25
> **Renée Jade said:**
> Hey all,

I use Ubuntu on my personal laptop and it really has nothing very important on it. So I would love to be able to change the access permissions on some commands so that I can execute them without sudo. I don't want to get rid of sudo completely though, it has saved me from some near disasters. So, using "poweroff" and "reboot" as examples, how can I make it so that I can execute them as renee instead of root?

The easiest way is to set the "setuid" flag on those commands:

```
sudo chmod +s /sbin/reboot
```

(I think that command should work... I've only ever tried it the GUI way using Nautilus' "Advanced Permissions" editor).

Setuid is a solution to the problem, but it's actually done the other way around to how you asked. Rather than the "reboot" command being run as renee, it actually happens that when renee tries to run the command, it will run as the file's owner - which in this case is root.

Setuid is a potential security problem because an attacker can sometimes gain a root shell after crashing a program that runs as setuid. Use Setuid sparingly.

---

### Post by Renée Jade on 2009-10-25
> **3rdalbum said:**
> The easiest way is to set the "setuid" flag on those commands:

```
sudo chmod +s /sbin/reboot
```(I think that command should work... I've only ever tried it the GUI way using Nautilus' "Advanced Permissions" editor).


I'm pretty sure this is what I'm after. I'll give it a shot.

>  Setuid is a solution to the problem, but it's actually done the other way around to how you asked. Rather than the "reboot" command being run as renee, it actually happens that when renee tries to run the command, it will run as the file's owner - which in this case is root.

Setuid is a potential security problem because an attacker can sometimes gain a root shell after crashing a program that runs as setuid. Use Setuid sparingly.Yeah, like I said - this computer is really just the hack victim and whatever happens to it happens to it. But good to know that it creates a vulnerability.

Cheers everyone :D

---

### Post by Renée Jade on 2009-10-25
> **3rdalbum said:**
> 
```
sudo chmod +s /sbin/reboot
```


Exactly what I wanted. Thank you! :D

---

