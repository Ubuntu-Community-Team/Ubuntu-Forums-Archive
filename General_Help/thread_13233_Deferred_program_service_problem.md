---
title: "Deferred program service problem"
date: 2005-01-29
forum: General Help
---

### Post by oracledarren on 2005-01-29
Hi

Hope somebody can help or explain what is happening.

I notice when starting my machine and when shutting down I get the error failed to start/stop deferred program service or something like that anyway.

Can anybody tell me what this is about please ?

Thanks

Darren

---

### Post by mendicant on 2005-01-30
Do you have the exact error message?  The screen output prior to that?  You can probably install a little init.d kill script that will pause your computer for a bit if you need more time to view the error.

---

### Post by oracledarren on 2005-01-30
I cant seem to slow it down is there a log that gets recorded anywhere that i could use an editor to get this information?

---

### Post by oracledarren on 2005-01-30
Got the error now.

while starting it says

Starting deferred execution scheduler [FAILED]

and when rebooting the same but 'stopping'

Hope someone can help :D

---

### Post by oracledarren on 2005-01-30
Anyone.... please :) ?

---

### Post by mendicant on 2005-01-30
That would be atd that's failing.  Do you have the atd daemon?  /usr/sbin/atd?

---

### Post by mendicant on 2005-01-30
Oh, and it's not really a big deal if you don't use at, although it is mildly suspicious.

---

### Post by oracledarren on 2005-01-30
Hi

thanks for that, yes that file is there.  What is the best way to remove whatever it is please ?

Thanks

Darren

---

### Post by oracledarren on 2005-01-30
What I have done for now which seems to have done the trick is remove the atd file from /etc/init.d  and that seems to correct it.

But I would like to know what program it belongs to in case the program is corrupted in some was and needs reinstallation.

If someone would let me know that would be great :D

---

### Post by mendicant on 2005-01-30
Well it belongs to the 'at' daemon.  Not sure why it would fail.  You can try starting it manually by doing /usr/sbin/atd -d and see what error messages you get.  You would need to be root, of course.  If that displays any additional data, you can post it here.

You can uninstall or reinstall package 'at':
% aptitude reinstall at
To see if that fixes it.

---

### Post by oracledarren on 2005-01-30
I worked out what is was and lets just say I really now hate micro-filters  :mrgreen:

---

### Post by TravisNewman on 2005-01-30
So for people who may run into the same problem, how did you fix it?

---

### Post by oracledarren on 2005-01-31
Replaced the microfilter on the adsl modem, thats all i had to do

---

