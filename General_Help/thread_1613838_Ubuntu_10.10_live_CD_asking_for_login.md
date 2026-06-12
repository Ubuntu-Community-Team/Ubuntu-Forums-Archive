---
title: "Ubuntu 10.10 live CD asking for login"
date: 2010-11-04
forum: General Help
---

### Post by zappadragon on 2010-11-04
Why is the live cd of Ubuntu 10.10 asking for a login and what is it?

---

### Post by dcstar on 2010-11-05
> **zappadragon said:**
> Why is the live cd of Ubuntu 10.10 asking for a login and what is it?

[LIST=1]
[*]It shouldn't - something is not working properly.
[*]User "Ubuntu", no password (IIRC).
[/LIST]

---

### Post by Kangarooo on 2011-01-27
WOW. i also just now experienced this with Ubuntu 10.10 CD with witch i have gone in Live mode and never been asked for username but now on one friends Fujitsu-Siemens AMD computer its asking for Login..
Username ubuntu and no password worked.
THX
to witch package this bug should be reported?

---

### Post by Tynictansol on 2011-03-06
Booting on a Toshiba Dynabook (1.3ghz celeron M/756MbRAM) it's asking for a username and password.  Ubuntu user with no password gives me an authentication error.  Any ideas?

---

### Post by dandnsmith on 2011-03-06
I've seen this happen with earlier releases and other distros where some resource (like the amount of RAM) wasn't sufficient. In my case it disappeared as a symptom when I increased the amount of RAM. Your amount looks a bit marginal - would have worked with 8.04 ...

HTH

---

### Post by sneetch on 2011-03-26
I have the same issue: The UBUNTU desktop installation disk asks for a username and a password. Using "Ubuntu" or "ubuntu" as username will not help. 

My configuration: 

[B]Dell Inspiron 6000 laptop
ATI X300 graphics (128Mb)
2Gb RAM 
150Gb Hard drive
High resolution display[/B]

I believe that should be enough to run UBUNTU, no? 

Thanks for any help...

---

### Post by linuxuser12345 on 2011-03-26
Have you tried this:
Username: ubuntu
Password: ubuntu

---

### Post by sneetch on 2011-03-29
Thanks for the reply. I have since figured out what the problem was: 

The laptop had a problem with the memory chip installed. I changed the memory (I didn't increase the mem!) to two 512Mb modules instead of two 1Gb modules and it works. 

I think that if you have faulty or wrong memory configurations in your computer, the UBUNTU desktop install CD will most likely not work properly.

---

### Post by BillGod on 2011-03-29
I have the same problem.  It's definitely not a RAM issue on this computer.  It boots up and logs me in.  then when the screen saver kicks on I am at the login screen asking for a password.  Blank does not work.  I have to reboot then set screen saver to NOT put you to login screen.

---

### Post by tredegar on 2011-03-29
The screensaver is not asking you to _login_.

It is asking for your password to _unlock the screen_.

You do not need to reboot: Just **System - Preferences - Screensaver**, and un-check "Lock screen when screensaver active".

---

