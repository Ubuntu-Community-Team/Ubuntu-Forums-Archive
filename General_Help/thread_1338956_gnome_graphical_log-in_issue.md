---
title: "gnome graphical log-in issue"
date: 2009-11-27
forum: General Help
---

### Post by Reston Marcus on 2009-11-27
Hi, 

New to Ubuntu & Linux.  Just received Karmic 9.10 in mail.  Excitedly, after reading all day, I partitioned then installed to dual boot Karmic with Win-7.  After some configuring I was prompted to reboot.  After the reboot, all seemed fine due to automatic log-in.  However, on the requested reboot from my alterations, the screen is now continuously provides command-line only boot in (!???!)

How can I correct this?  How can I stop this from recurring?  Please Help.  

I have looked at a lot of threads since I joined trying to narrow searches to this specific type of issue with no immediate solution.  Again, Please Help.

---

### Post by aysiu on 2009-11-29
Does logging in and then typing ```
sudo /etc/init.d/gdm start
``` help?

---

### Post by Reston Marcus on 2009-11-30
Very excited will try it right now and get back you.  Today!

---

### Post by Reston Marcus on 2009-11-30
First of all, Thank You!

The response I got from your suggestion:

"Since the script you are attempting to invoke has connected to an upstart job, you may also use the start (8) utility, e.g. start gdm gdm start/running, process 2181"

Out of curiosity I pressed enter and got:

"no set id found" 

Also,

"Failed to acquire org.gnome.displaymanager connection "1:20" is not allowed to own the service due to security policies in configuration file."

Which made me wonder if I did too much configuring before third reboot because i was not invoked to do so -- I installed compiz, and associated stuff.  Seemed to work flawlessly.  Until that reboot that led me to here.  Additionally, I did not (due to uncertainty of outcome) invoke the graphical password login which I regret.

Also my laptop requires a lot of drivers (don't care about that now.  Could use web browser & majority of functions work to my amazment).  Lenovo t400 -- ultra loaded -- dual booting win-7.

I admit, I'm ignorant (for now) to the command-line.  Will not be for long.  But I want to completely switch (someday soon); saved off-line the complete LinuxCommand.org site. But I'm still a slave to a GUI for present productivity reasons too.

Your aid (and other empirically gifted in the forum) is more than Most Welcome!

---

### Post by mikewhatever on 2009-12-05
> **Reston Marcus said:**
> ...............

Which made me wonder if I did too much configuring before third reboot because i was not invoked to do so -- I installed compiz, and associated stuff.  Seemed to work flawlessly.  Until that reboot that led me to here.  Additionally, I did not (due to uncertainty of outcome) invoke the graphical password login which I regret.

.................

What else did you do other then installing compiz? You keep throwing these vague 'configuration, alteration and association' terms around, which aren't helping anyone to help you.

---

