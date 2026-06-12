---
title: "udev worker did not accept kill it"
date: 2010-05-25
forum: General Help
---

### Post by hangfire on 2010-05-25
Booting 10.04 today, I got a message like this for several seconds:

udev worker (some number) did not accept ... kill it

It does not show up in **dmesg** or anything else in **/var/log/***.

Apparently this is a known udev message but not commonly encountered.

No recent message I've posted here has received any attention, but I throw this out here anyway.

-HF

---

### Post by hangfire on 2010-05-28
Bump.

---

### Post by hangfire on 2010-06-02
Got a different udev error on boot yesterday.. since no one cares, didn't bother to write it down.

---

### Post by ArmchairArmada on 2010-07-06
I just got a similar message to this.  While booting the screen was filled with these messages.  Is it something to be concerned about?

---

### Post by Sjenitzer on 2010-08-06
same here about 272 worker did not accept it, but apparently it is not something to worry about???

I am running Ubuntu 10.04

---

### Post by Cowchip7 on 2010-08-28
Bump. Same problem.

---

### Post by Copro on 2010-10-14
There is a similar bug logged on Launchpag here:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/647404](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/647404)
Udev worker error during boot "worker [XX]  did not accept message -1 (Connection refused), kill it 

You should be able to track and add your problems there if it fits.

---

### Post by mikitz on 2011-02-22
So a worker doesn't accept a job so we just... kill it!? Oh the humanity.. no wonder why everyone is trying to sweep this one under the rug!

:-#

---

### Post by mbrinson on 2011-08-06
> **mikitz said:**
> So a worker doesn't accept a job so we just... kill it!? Oh the humanity.. no wonder why everyone is trying to sweep this one under the rug!

:-#

I know this is old, but I just had to say that comment was hillarious mikitz!  Had me laughing out loud.

Still have this issue, but at least I'm smiling about it now.

---

### Post by saraanine on 2011-08-27
Hi, can anyone explain in plain English (for a non-techie on 10.4) if it is problematic that, when I boot up, I am receiving the "kill it" message referenced in this thread. If it is a problem, how do I fix it? Thanks.

---

