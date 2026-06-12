---
title: "problem"
date: 2012-10-14
forum: General Help
---

### Post by padelos on 2012-10-14
Hi ,

i have problem with my pc when it shut down

it puts out : _**speech - dispatcher disabled/ edit/etc/default/speech;dispatcher**_

with result doesnt closing the computer

Please help me

---

### Post by ajgreeny on 2012-10-14
What does that file contain?

Let us see the output of ```
cat /etc/default/speech-dispatcher
```

---

### Post by padelos on 2012-10-14
nothing 

It write : 

could not write bytes: brozen pipe
*starting crash report submision daemon
*stopping save kernel messages
*starting anac(n )ronistic cron
*stopping anac(n )ronistic cron
*checking batery state
*stopping system V runlevel campatibility

checking for running unattended - upgrades :[U][B] speech - dispatcher disabled;  edit/etc/default/speech-dispatcher

[/B]what i do??[/U]

---

### Post by ajgreeny on 2012-10-14
See if you have speech-dispatcher installed with ```
sudo apt-get install speech-dispatcher
``` which will just tell you that it is already the latest version if you already have it.  If you do already have it, it may be worth reinstalling with ```
sudo apt-get install --reinstall speech-dispatcher
``` to see if that configures it properly.

---

### Post by padelos on 2012-10-14
hi 

I have tried these items and nothing

The only solution is  reinstalling

---

