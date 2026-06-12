---
title: "Are 'half-installed' and 'half-configured' packages ever OK?"
date: 2011-06-16
forum: General Help
---

### Post by knidsrok on 2011-06-16
So, while working some of the kinks out of my new Natty installation, some of the advice dispensed in prior threads from this folder led me to take a look at the dpkg.log file in /var/log.

There are a fair number of packages whose status is listed as "half configured" or "half installed." Is every instance of this a problem of some sort, or are some packages listed in the dpkg.log *supposed* to be left half installed or configured?

---

### Post by andrewthomas on 2011-06-17
No 

sudo dpkg --configure -a

---

### Post by knidsrok on 2011-06-17
Before I saw your response, again going off of prior threads, I tried reinstalling dpkg thus:

sudo apt-get install --reinstall dpkg

It seems to have solved all the issues I was having with fake initctl and fake start-stop daemons.  I figure it probably ended up reconfiguring all packages in the process, and thus was a sort of round about way of doing what you suggested.

Either way, problem solved, and thanks.

---

### Post by rtimai on 2012-04-15
I recently noticed an alarming number of packages in my /var/log/dpkg.log with Status half-configured. I am not noticing any symptoms, except that ClipIt clipboard manager no longer appears to save buffer contents. Please see attachment for the grepped list.

I ran: 
sudo dpkg --configure -a

...after entering the password nothing appeared to happen, I was immediately returned to the command line with no message.

I also re-installed dpkg in Synaptic Package Manager and rebooted, and still see the same packages half-configured (not sure if I need to do anything to refresh the log.)

Should I be concerned?

UPDATE:
Half-configured packages are no longer in the current /var/log/dpkg.log after upgrade to Ubuntu 12.04 Precise Pangolin.

---

