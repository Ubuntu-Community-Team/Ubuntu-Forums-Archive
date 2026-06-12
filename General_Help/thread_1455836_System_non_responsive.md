---
title: "System non responsive"
date: 2010-04-16
forum: General Help
---

### Post by Panik on 2010-04-16
Currently running Ubuntu 9.10 64bit

Generally the system is stable while being used, but for some reason, if the computer has not been used for an extended perioud (30 minutes or more), sometimes the screens are black, and they will not come back on through keyboard or mouse presses, and I am forced to cold restart the computer.  In addition, it appears the computer may be "locked up" if you will, because I see no response on the keyboard lites when I press "Caps Lock" or "Num Lock", eg, the lights on the keyboard to not change.  

Often times, several people have been "logged into" the computer.  My entire family uses this computer so several people could technically be logged in (if that makes any sense).

Obviously, I am a newb.  Not sure how I can better explain.

-Jim

---

### Post by Panik on 2010-04-16
Any ideas?????

---

### Post by RedSingularity on 2010-04-16
Is this problem when the screensaver engages?  Thats when the screen is usually black.

---

### Post by commanderzhao on 2010-04-16
that happens to me too sometimes
there is only one user account on my laptop
but my mom and I use the same user:guitar:
good luck

---

### Post by commanderzhao on 2010-04-16
> **RedSingularity said:**
> Is this problem when the screensaver engages?  Thats when the screen is usually black.
no It's after that

---

### Post by RedSingularity on 2010-04-16
What if you disengage the screensaver?  Does it prevent the lockups?

---

### Post by quadproc on 2010-04-16
> **Panik said:**
> Currently running Ubuntu 9.10 64bit

Generally the system is stable while being used, but for some reason, if the computer has not been used for an extended perioud (30 minutes or more), sometimes the screens are black, and they will not come back on through keyboard or mouse presses, and I am forced to cold restart the computer. 
I am running the same version and I had the same kind of lockup under the same conditions.  It only happened once and I was unable to figure out why.

You might learn something by looking in the various logs, especially the system log, in /var/log.  If a problem is logged it will probably be in the last few entries so a tail -n 50 syslog might be useful.

One other quastion: is your system connected to something like a LAN, an X windows terminal, or anything else that might have been using remote access to your system?

Sorry that I don't have an answer, just a suggestion that might help to figure it out.

quadproc

---

### Post by Panik on 2010-04-16
> **quadproc said:**
> I am running the same version and I had the same kind of lockup under the same conditions.  It only happened once and I was unable to figure out why.

You might learn something by looking in the various logs, especially the system log, in /var/log.  If a problem is logged it will probably be in the last few entries so a tail -n 50 syslog might be useful.

One other quastion: is your system connected to something like a LAN, an X windows terminal, or anything else that might have been using remote access to your system?

Sorry that I don't have an answer, just a suggestion that might help to figure it out.

quadproc

I will look at the logs when it happens again.

My computer is on a LAN, and I run slimserver for my squeezebox.  The system also accesses a ReadyNAS nv+.

---

