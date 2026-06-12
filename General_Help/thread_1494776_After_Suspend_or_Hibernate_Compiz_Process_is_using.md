---
title: "After Suspend or Hibernate Compiz Process is using 75%+ procsessor"
date: 2010-05-27
forum: General Help
---

### Post by igmo169 on 2010-05-27
Hello,

 I have 10.04 installed on my Laptop (Dell Latitude D630 with the Nvidia video upgrade). This was a clean install to a hard drive that I let it totally erase and use as it saw fit. I am using the Nvidia driver marked as "current" in the hardware driver settings.

When my laptop screen dims due to inactivity, such as not used for 5 mins or so, it will prompt me for a password to log back in.  No big deal.  However, when it resumes from this state it is SLOW!!  I go to system monitor and see that the process "Compiz" is burning up both of my cores at about 70% or HIGHER.  It's not using a significant amount of memory which is strange.

From what I have been able to gather Compiz has some responsibilty for the GUI and killing the process to attempt to restart it is a "bad idea" (tried that lol).

This also occurs when the laptop hibernates.

I see that there are various posts referencing hibernate/suspend issues but, I am still getting my feet wet with some of the terminology here so some of them hurt my brain. Any help would be appreciated.

Thanks,
iGmO

---

### Post by igmo169 on 2010-05-27
I will actually add that Compiz will continue to eat up processor until I reboot the machine. This of course annihilates battery life and generates a lot of heat.

 Is there anyway to reset compiz without a reboot? A script or something I can use after I come from suspend/hibernate?

Thanks,
igmo

---

### Post by ajgreeny on 2010-05-27
```
metacity --replace
``` in the run dialog (Alt+F2) will stop compiz and start metacity and you can then use ```
compiz --replace
``` to start compiz again.

The easiest way though is to get **compiz-switch** from [Forlong]("http://forlong.blogage.de/entries/pages/Compiz-Switch") and use that.  All it needs is a single click to turn compiz on and off.

---

### Post by igmo169 on 2010-05-27
Thanks I'll give that a shot!

---

### Post by igmo169 on 2010-05-29
Thanks a bunch, using that program to switch off compiz and then back on immediately does the trick!

You da man.

iGmO

---

### Post by 0janek on 2010-06-09
This looks like a bug in compiz. I experience the same symptoms on a desktop amd64 with geforce 7050: after longer suspend (few hours) it eats about 80% of CPU. Lucid, fresh install. Disabling compiz helps.

---

### Post by John Baptist on 2010-07-14
0janek: this happens to me too. It only seems to happen after long suspends. I am using nvidia drivers on Lucid, and didn't have a similar problem under Jaunty. Restarting compiz doesn't help; neither does restarting X entirely: I have to reboot the whole system. Does that correspond with your experience? Is there a launchpad bug for this?

---

### Post by jjgist on 2011-05-20
It's been a while since the last post on this thread but i am having the same problem with 11.04. did anyone ever find out the cause of this. compiz-switch doesn't work in natty.

---

### Post by dpjoff on 2012-01-12
:popcorn: waiting patiently for anyone to answer the thread. I am going to have to write something to auto kill it from cron I guess. :confused:

---

