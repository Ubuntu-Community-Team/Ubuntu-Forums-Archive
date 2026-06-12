---
title: "Thunderbird 3.1.15  Only one user allowed?"
date: 2011-11-23
forum: General Help
---

### Post by Alligator on 2011-11-23
Since upgrading to 3.1.15, I've noticed that two user accounts cannot both have Thunderbird running.  Error from 2nd user states that Thunderbird is currently running and you need to remove it or restart.  In other versions this was not an issue.  My wife can't check her email and I'm in trouble. Please help.

Thanks
Ron

---

### Post by Paddy Landau on 2011-11-29
Do you mean running *at the same time*? In other words, you open Thunderbird; switch user to your wife; she opens Thunderbird and gets the error?

---

### Post by Alligator on 2011-12-28
Sorry for the delay.
Yes, she will exit Thunderbird, I have it always running.  Then tries to start and the error results.  Checked processes and Thunderbird is running.  So, I kill the process and restart Thunderbird.

---

### Post by Paddy Landau on 2011-12-29
Hmm, that's puzzling. I've just tried and I had no problem. I'm running Thunderbird 3.1.16 on 11.04. Which version of Ubuntu are you using? Perhaps you want to run the updates to get the later version of Thunderbird and try again?

---

### Post by Alligator on 2011-12-29
I'm using Ubuntu 11.04, Kernel Linux 2.6.38-8-generic and GNOME 2.32.1

Typically T should be sleeping, but when the error occurs, I've checked the system monitor to find that it is running.  

My system has dual HD's mirroring each other. (RAID 1) Upgrading to the next release is something that I will have done by people more knowledgeable than I.

---

### Post by Paddy Landau on 2011-12-29
I have 11.04, Kernel 2.6.38-13-generic, Gnome 2.32.1.

I was not suggesting you upgrade to the next distribution, but just run the normal updates. Open Update Manager; select Check; select Install Updates. It should update your Thunderbird to 3.1.16. You will have to restart after updating as you have an older kernel.

After restarting, try again to see if the problem recurs.

---

### Post by Alligator on 2011-12-31
This is the version currently installed = 3.1.16+build2+nobinonly-0ubuntu0.11.04.1 (thunderbird)

I exited Thunderbird in order to run the Update Manager - no updates required. Then started T. and got the error. System monitor showed T. was "running" not "sleeping"

---

### Post by Paddy Landau on 2011-12-31
Hmm, I wonder why your Thunderbird is running and not sleeping? It may be downloading emails?

I'm sorry, I cannot help -- I don't understand why you have the problem, because mine seems to work fine.

---

