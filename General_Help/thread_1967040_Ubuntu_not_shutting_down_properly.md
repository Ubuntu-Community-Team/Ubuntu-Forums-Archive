---
title: "Ubuntu not shutting down properly"
date: 2012-04-27
forum: General Help
---

### Post by wagnebr1 on 2012-04-27
Hi,

For a few months, when I command the system to "Shut Down" from the  on-button (upper right corner), it reverts to the user login screen and never shuts down.  I am forced to do a hard shut down.  I would like to have my system shut down properly when I tell it to, rather than guessing if it will, then risking a wrecked HD because it didn't.

Any ideas on how to fix this?  Anyone else seen this?

Thanks

---

### Post by mc4man on 2012-04-27
Have only seen here, (being thrown to login) when there is more than 1 user logged in.

If that's not the case for you thenI do recollect some report about a single user login being returned to login screen, will post in if I find.

(on my 32 bit install with nvidia, I get a failed restart/shutdown with the 205.XX drivers but's that's a rare corner case bug & 64 bit works fine

---

### Post by mode7 on 2012-04-27
I once had this issue. I cannot remember what fixed it, but I am pretty sure it was something along the lines of X crashing and restarting the login manager before shutting down.

I would try enabling proprietary drivers, if available, or disabling them if they are already installed.
Installing updates always helps too ;)

Does shutting down using 'sudo shutdown -h now' from a terminal work?

---

### Post by wagnebr1 on 2012-04-28
It is not consistent about when it "hangs up".  By that I mean, it has given me problems with 1,2, or 0 users logged in.  

Some times it works, sometimes it doesn't.  

I have not tried the terminal shutdown command yet.
Also, I have not tried disabling proprietary drivers.  This is not a solution I could get very excited about.

As for system updates, I check for updates (and install them) daily.

Thanks;)

---

### Post by wagnebr1 on 2012-04-30
> **wagnebr1 said:**
> It is not consistent about when it "hangs up".  By that I mean, it has given me problems with 1,2, or 0 users logged in.  

Some times it works, sometimes it doesn't.  

I have not tried the terminal shutdown command yet.
Also, I have not tried disabling proprietary drivers.  This is not a solution I could get very excited about.

As for system updates, I check for updates (and install them) daily.

Thanks;)

Further details .....

I'm running a dual boot machine with Win7, on a Dell Inspiron 15R laptop with Intel i3 processor.  My ubuntu version is 11.10 64-bit, despite what it says in the user profile.  I have not updgraded to 12.04 yet, but will do it in the next few weeks.

The same thing happened again last night as I was shutting it down for bedtime.  I made sure only one user was logged in (me) and did a shut down by selecting it from the "power" button in the upper right-hand corner.  It dumped me to the user login screen and stopped.  I then selected shut-down again from the "power" menu and it did nothing.  I had to turn the power off with a hard shut-down (4th time this week....grrrr).

New ideas?  I have no idea where to go from here.   This is the kind of stuff that makes me want to quit trying to make Ubuntu work for me and ditch it all together.

---

