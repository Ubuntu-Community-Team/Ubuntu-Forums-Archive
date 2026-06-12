---
title: "Phantom monitor"
date: 2012-06-04
forum: General Help
---

### Post by willisdl on 2012-06-04
Hi,
   I'm running 10.04 (yes, I know, I need to upgrade - in my copious free time...), and I'm having a problem with my monitor setup.  Until recently, my monitor showed up as "Unknown" which wasn't a problem, since everything worked.  Suddenly, in the last week or so, a second monitor has appeared in my monitor preferences - a Dell 15", which I don't have and has never been connected to the computer.  Worse, if I leave the real monitor powered off for any length of time, or VNC into the computer (which I do when I'm on the road), Ubuntu autodetects monitors and deletes the "unknown", leaving only the ghost Dell.  Of course, this means that when I turn the monitor on, the computer no longer outputs to it, so I get no signal, and have to VNC in from a second computer while the monitor is turned on and tell it to detect monitors.

Anyone know where this phantom monitor came from?  And how do I get rid of it so the computer will only use the real monitor?  Thanks.

Dave

---

### Post by Paddy Landau on 2012-06-05
Unfortunately, I do not know the solution to your problem.

However, in your place I would try going into the Monitor settings (sorry, I don't remember the menu options to get there in 10.04). Choose your correct monitor and check the settings; then choose your phantom monitor and turn it off.

I hope that helps.

---

### Post by IWantFroyo on 2012-06-05
System->Settings->Monitors (I think)
 
You should be able to simply delete the phantom monitor from there.

---

### Post by willisdl on 2012-06-14
I did go into the Monitors section under system settings and turned off my mystery monitor.  One thing I discovered is that if I leave the real monitor powered off for more than an hour or so, Ubuntu reactivates the mystery monitor, and then I have to ssh into it from another computer and set the main monitor back to the actual hardware.  As yet, I have discovered no way to actually delete the monitor.

I went ahead and upgraded to 12.04, hoping that might solve the problem, but no luck.

---

### Post by Paddy Landau on 2012-06-14
Did you upgrade or do a fresh installation?

---

### Post by willisdl on 2012-06-15
I upgraded - I'm trying to avoid a fresh install, since this machine is my media server for the house.  And since I don't know what's causing the issue, I'm worried that I'll spend all that time to do a fresh install, only to have the same thing occur again.

I'd really like to figure out what the cause of the whole issue is - and why it's only started recently, when I've had this system running for almost a year.

---

### Post by Paddy Landau on 2012-06-16
I really can't tell you what causes the problem. However, if you boot 12.04 from a Live CD (or Live USB), you will be able to tell whether or not the problem recurs. If it does not recur, you may find that a fresh installation (after a full backup, of course), will solve the problem.

---

