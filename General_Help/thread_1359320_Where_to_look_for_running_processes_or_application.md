---
title: "Where to look for running processes or applications"
date: 2009-12-19
forum: General Help
---

### Post by webbdawg on 2009-12-19
I recently have been trying to upgrade Firefox 3.0.15 to 3.5.6 and ended up just closing it.

Later I tried to start it again and I got the message that it was already running and I would have to shut it down or reboot.

SO I just logged out and logged back in and I was able to close in on restart.

Where do you look for running processes like crtl>alt>delete in windoz?? So I can shut down processes or applications that are stuck.

Thanks
Dave

---

### Post by nitstorm on 2009-12-19
try this

system-->administration-->system monitor
click on the processes tab

u can choose to end the process by clicking on end process,

u can also try the following code in the terminal:

killall firefox

that will kill all instances of firefox

hope that helped

---

### Post by turvyc on 2009-12-19
You can also try this command:
```
top
```
It gives you your top processes.

Also, you can try:
```
ps aux | grep firefox
```
With these two, you can get the process ID (pid) of the process, and kill it using
```
kill <pid>
```
Honestly, though, I've been having the same weirdness with Firefox. Sometimes none of these tricks work, and I am forced to either restart my session or use my backup browser (currently Epiphany).

---

### Post by Barriehie on 2009-12-19
Can also, from the terminal,
```

ps -u *username*
```
and if you know the name of the process:
```

ps -u *username* | grep *process_name*

```

Barrie

---

### Post by webbdawg on 2009-12-19
Thanks

I knew it was close by

Dave

---

