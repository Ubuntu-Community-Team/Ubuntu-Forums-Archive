---
title: "Kubuntu 11.04 keeps crashing :("
date: 2011-08-10
forum: General Help
---

### Post by linuxuser12345 on 2011-08-10
I just installed Kubuntu 11.04 on my netbook, and it is acting up more than what Windows 7 Starter would! :(
Every time I enable the visual effects, things start to run so slow that it automatically disables them again, and every time I go to change the desktop background, either the desktop goes blank or the x server crashes completely and restarts.

Kubuntu 10.10 and Ubuntu 11.04 work just fine, but I like the driver support and features that Kubuntu 11.04 has. 

Is there any way I can fix this problem??

---

### Post by linuxuser12345 on 2011-08-10
PS: I already updated. It didn't help at all. :/

---

### Post by linuxuser12345 on 2011-08-11
Can anyone help?? I already tried searching Yahoo.com, but no luck... :/

---

### Post by samigina on 2011-08-11
A netbook isnt the best machine for KDE.

We can start looking at your logs, specially the X logs. There we will see what is going wrong.

---

### Post by linuxuser12345 on 2011-08-11
How do I do that? Kubuntu 10.10 and 10.04.3 work fine on it, but Kubuntu 11.04 doesn't very well :(
Kubuntu has better driver support, too...

---

### Post by samigina on 2011-08-11
Just type "log" in your main or "start" menu (kickoff), you will find an app called **ksyslog**, in that app you can see the system logs, search for the last time you suffered a freeze and probably we will get more info about the problem.

---

### Post by linuxuser12345 on 2011-08-11
The actions of enabling the desktop effects and the computer disabling them are not being recorded to the System Log... :/
Now what?

---

### Post by linuxuser12345 on 2011-08-11
Maybe I can search up using a keyword to find something that might be disabling them, or causing the system to run slow when they are on for the short period?

---

### Post by samigina on 2011-08-11
Look for things related to X SErver, Segfaults, Kwin...

At the top theres some controls to set wich logs you see, be sure to take a look to almost all of them.

With the log viewer opened, try to reproduce the actions that has crashed your system before.

Be patience, Im sure we will find whats the problem.

I almost forget to ask something pretty important. Whats your graphic card? What driver are you using?

Oh, and please excuse me for my english.

---

### Post by linuxuser12345 on 2011-08-11
It is a netbook, so it is probably some integrated Intel graphics chip or something.

---

