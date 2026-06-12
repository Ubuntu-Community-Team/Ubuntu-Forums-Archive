---
title: "Automaticly Boot and shutdown my server"
date: 2011-02-18
forum: General Help
---

### Post by thyvo on 2011-02-18
Hello,
I got a question, is there a script or program that automaticly boots my server and shutdown at give hours of a day
I want to have my server running from 7am till 8pm ever weekday (Monday-Tuesday-Wednesday-Thursday-Friday)
is this possible?
I'm running a Ubuntu 10.04 server with Zentyal on

---

### Post by Sean Moran on 2011-02-18
> **thyvo said:**
> Hello,
I got a question, is there a script or program that automaticly boots my server and shutdown at give hours of a day
I want to have my server running from 7am till 8pm ever weekday (Monday-Tuesday-Wednesday-Thursday-Friday)
is this possible?
I'm running a Ubuntu 10.04 server with Zentyal on
I believe that cron will do the shutting down part, but booting again is a different agenda.  Are you looking to completely shutdown all power as in switch-off, or just hibernate for 11 hours?  I reckon there are utilities that could do the hibernate, and restart, but Ubuntu seems to do the hibernate fairly normally already, until you hit a key to wake it up.

I am sure there are utilities in the Software Center that can handle this, but switching off completely, might be another matter.  What are you hoping to achieve beyond the standard hibernation?

---

### Post by HermanAB on 2011-02-18
Just leave it running.  That is what it is designed to do.

---

### Post by thyvo on 2011-02-18
> **Sean Moran said:**
> I believe that cron will do the shutting down part, but booting again is a different agenda.  Are you looking to completely shutdown all power as in switch-off, or just hibernate for 11 hours?  I reckon there are utilities that could do the hibernate, and restart, but Ubuntu seems to do the hibernate fairly normally already, until you hit a key to wake it up.

I am sure there are utilities in the Software Center that can handle this, but switching off completely, might be another matter.  What are you hoping to achieve beyond the standard hibernation?
I'm just want to find a way to reduce my power consumption cause only the server will be accessed between those hours
its a file and printer server for a small business
just a way to reduce the energy bill :p

---

### Post by thyvo on 2011-02-18
> **HermanAB said:**
> Just leave it running.  That is what it is designed to do.
if my costumer asks to it down to reduce power consumtion, I'm going to try to do that

---

### Post by QLee on 2011-02-18
So are you doing this as a technician for a client?

Setup in the BIOS a time to auto start the machine, then use the suggestion of a cronjob to shut it down, seems a fairly straightforward thing to try. It appears to meet your specifications.

---

### Post by megabuffen on 2011-02-18
Here is some information about automatic shutdown sing cron:
[http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html](http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html)

As for powering up again, it's not easy to run commands on a computer that is turned off. What you can try is installing a timer that physically removes power from you computer for 15 minutes or so in the morning, and configure the BIOS to automatically start when power is resupplied. Go into your BIOS setup and look for that option. You should be able to test it by removing the power cord and plugging it back in. The computer should then boot automatically. This is what I have done with my server to make it come back online after a possible blackout, or if someone decides to borrow a wall outlet...

Make sure that you only remove power for a few minutes prior to startup. Leaving the power off during the whole night will just make the motherboard clock battery drain faster. Also, make sure that the computer is turned off by cron before the timer kicks in. Turning it off every day by removing power is obviously a really bad idea.

---

