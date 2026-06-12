---
title: "run sudo without passord HELP!!!!"
date: 2011-08-02
forum: General Help
---

### Post by pastet89 on 2011-08-02
Hi. 
I have read about 10 treads already and no matter what I try, I can not get this working.

My goal:
[http://ubuntuforums.org/showthread.php?t=140696](http://ubuntuforums.org/showthread.php?t=140696)

My specific case:

I have created a script /home/pastet/nomouse.sh

which contains the lines 

```
#!/bin/bash
sudo modprobe -r psmouse

```

On the end of the file visudo I put:

```
pastet ALL=NOPASSWD: /home/pastet/nomouse.sh

```

and in the startup programs I put:

bash /home/pastet/nomouse.sh

(Bash is the correct execution command for .sh on my computer, I have tested and the script works with it).

I am usung 9.10

Please, HELP!!!!

---

### Post by Bonster on 2011-08-02
I believe u have to do that for the command not the script itself

so maybe try:

> pastet ALL=NOPASSWD: /sbin/modprobe

---

### Post by Spyderkid on 2011-08-02
the password is there for a reason, don't try to avoid it.

if your using sudo alot use sudo su so you only have to enter it once for that session

---

### Post by pastet89 on 2011-08-02
@Bonster - it worked!!! thank you m8!!
@Spyderkid - don't worry, its only to stop the touch pad on load, so to kill that anoying problem with the jumping cursor while typing ;)

---

### Post by aeiah on 2011-08-02
is this just something you need to load only once upon startup? if so, id have just added 'modprobe -r psmouse' to /etc/rc.local - this gets executed by root at boot time

---

