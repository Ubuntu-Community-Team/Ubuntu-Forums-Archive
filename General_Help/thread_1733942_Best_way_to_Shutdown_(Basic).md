---
title: "Best way to Shutdown (Basic)"
date: 2011-04-19
forum: General Help
---

### Post by Matt Pellegrini on 2011-04-19
Naturally i don't want to harm my system but i would like i shutdown via  the terminal. I understand there are shutdown poweroff and halt  commands. Which is the safe one (like as if i just did it using the GUI)  at the moment i am just using shutdown now and that seems to work fine,  i just want to check that it's not harming my system and that this  command does everything it needs to ie closes all programs and shuts  everything down in a safe way.
Thanks in advance, sorry this is so basic.

---

### Post by ondemanddesign on 2011-04-19
I use 
```
sudo shutdown now
```
or
```
sudo reboot now
```

This is safe.

References to manuals:
[http://linux.die.net/man/8/shutdown](http://linux.die.net/man/8/shutdown)
[http://linux.die.net/man/8/reboot](http://linux.die.net/man/8/reboot)

or type the following in the terminal

```
man reboot
```
or 
```
man shutdown
```

---

### Post by dcstar on 2011-04-20
> **ondemanddesign said:**
> I use 
```
sudo shutdown now
```
or
```
sudo reboot now
```
..........

For those that want to save a keystroke or two:

```
sudo init 0
sudo init 6
```

---

### Post by TheCosmicFrog on 2011-04-20
```
sudo shutdown -P now
```

Shuts down (shutdown) and powers off the machine (-P).

---

### Post by Grenage on 2011-04-20
> **TheCosmicFrog said:**
> ```
sudo shutdown -P now
```

Shuts down (shutdown) and powers off the machine (-P).

I use:

```
sudo shutdown -h -P now
```

h is already implied, so I don't know why I still use it...

Which is probably identical to:

```
sudo shutdown now
```

---

### Post by djwkd on 2011-04-20
```
sudo shutdown now
``` only puts the computer in maintenance mode (or whatever its called). It does not power it off. 

```
sudo shutdown -P now
``` is what you need to shut it down exactly then. You can also time it. For example,

```
sudo shutdown -P 15:30
``` will shut down and power off at 3-30PM. You can also do it in minutes:

```
sudo shutdown -P 25
``` will power it off in 25 minutes (if my memory serves me correctly). Its a very handy command to use if you're leaving something to upload/download or render overnight, but it might only need an extra 2 hours or so.

---

### Post by Spyderkid on 2011-04-20
also this is a nice feature of ubuntu which you don't get on windows.

briefly press the big power button on the computer and then press enter.


not sure if you needed to know that or not but it might be usefull

---

