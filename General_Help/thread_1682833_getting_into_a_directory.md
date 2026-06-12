---
title: "getting into a directory"
date: 2011-02-06
forum: General Help
---

### Post by Spiritof76 on 2011-02-06
I am trying to get into a directory on my server, that is owned by root.  
```
drwx------  2 www-data www-data  4096 2010-06-01 17:32 images
```
if I type in
```
cd image/
```

I am informed that I don't have permission.

If I type in 
```
sudo cd image/ 
```

I am informed that 
```
sudo: cd: command not found
```
why would this be, and how can I get sudo cd to work?

---

### Post by stlsaint on 2011-02-06
the command:

```
cd
```

is not a program so you do not "run" it as you would say apt-get or aptitude with 

```
sudo apt-get install
```

i would just suggest using 

```
sudo -i 
``` 

and editing the directory as needed then run

```
exit
``` 

to get back to user prompt.

---

### Post by khelben1979 on 2011-02-06
I would recommend you look up: **File Manager - Super User Mode** and then go into that directory graphically. It would be the easiest thing.

Otherwise, ```
man sudo
``` to know how you use the command.

---

### Post by DarthScape on 2011-02-06
You could just try using su instead of sudo. Might be easier.

---

### Post by Spiritof76 on 2011-02-06
Thanks all:
sudo -i
did the trick.
su
Didn't work. It asked for a password, and it wouldn't accept my user password. I assume because I never never created a root password.
I tried 
sudo su
and that worked also.

I didn't realize the the command cd was handled differently than other commands and isn't a real program. I will mark this as solved. 
:guitar:

---

### Post by sdowney717 on 2011-02-06
gksu nautilus 
will open the file manager as root

---

### Post by Spiritof76 on 2011-02-06
> **sdowney717 said:**
> gksu nautilus 
will open the file manager as root

I thought of that, but I'm logged into the server via ssh from my desktop.  So I think I'm limited to the command line. and I haven't figured out how to explore my server from the desktop console.
Yet.

---

