---
title: "Can't shut down"
date: 2009-11-18
forum: General Help
---

### Post by Gavagai80 on 2009-11-18
When I click shutdown from KDE (Kubuntu 9.10), the first time it shows the 30 second prompt, which disappears when I click it. Subsequent attempts, clicking shutdown just doesn't do anything, no prompt.

Doing "sudo shutdown -P 1" from a terminal works.

This isn't an entirely consistent problem. Some days I've been able to shut down from KDE. Not now though, no matter how many times I do it from the terminal.

Also, I get a weird
"Trying to migrate 'resource'
Migration of 'resource' succeeded"
box for a minute after KDE startup every time, though it goes away on its own.

---

### Post by garvinrick4 on 2009-11-18
What does Code:   sudo shutdown -h now                     ---------for shutdown


or             Code:   sudo shutdown -r now                     -------- for reboot


Let me know if it solves.


When all else fails try.      alt/sys rq/b            ------in that order for reboot.

---

### Post by Gavagai80 on 2009-11-18
As I said in the first post, console-based shutdown works fine -- but on reboot after that, KDE still can't shut down from the visual menu item. Doesn't it indicate a problem when KDE's shutdown option doesn't work?

---

### Post by garvinrick4 on 2009-11-18
I believe it means that the GUI's trigger for that function is not working.
Isn't the GUI's job to give the command to the system software the same
as if you typed it in by hand.  So some where from one to the other is not
getting a command.

It sure seems like it indicates a problem when KDE's shutdown option doesn't work.
You are right

Sorry I misunderstood your 1st post, I will stay away from your Threads.

---

