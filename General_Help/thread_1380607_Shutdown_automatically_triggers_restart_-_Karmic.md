---
title: "Shutdown automatically triggers restart - Karmic"
date: 2010-01-13
forum: General Help
---

### Post by mamcoby on 2010-01-13
[FONT="Arial"][FONT="Arial"]I am using Ubuntu 9.10 (Karmic) on my Toshiba laptop (AMD64).

I recently upgraded from 9.04 and ever since whenever I try to shutdown, the laptop automatically restarts.

I tried this number of ways...
a. Using the power button in the top taskbar and using Shutdown option
b. In the Power management, I set the Laptop close lid action to Shutdown
c. In the login screen, tried clicking on shutdown.
no luck in either way.... the machine restarts everytime.

Any help would be highly appreciated.[/FONT][/FONT]

---

### Post by djs001 on 2010-01-13
I have this same issue

---

### Post by garvinrick4 on 2010-01-13
What happens with CODE:
 
sudo shutdown -h now

---

### Post by XRayA4T on 2010-01-14
> **garvinrick4 said:**
> What happens with CODE:
 
sudo shutdown -h now

Thanks, that worked for me.

---

### Post by mamcoby on 2010-01-14
> **garvinrick4 said:**
> What happens with CODE:
 
sudo shutdown -h now

Nope... sudo shutdown -h now ..also caused the laptop to restart instead of shutdown.

---

### Post by mamcoby on 2010-01-16
Can somebody please help me? This thing is driving me crazy !

---

### Post by mamcoby on 2010-01-22
Somehow I dont understand it is something that the way I post my issues or the issues I post are so stupid enough that no one bothers to even try to look at it.

This is my second post and both posts were so conveniently ignored by the whole team (who I am sure that are more than capable of resolving complex to complex issues, as I have seen in other posts)...

Anyhow.. for all those newbies like me facing this problem, here is how I could finally go about resolving the issue.

After some tiring research, I found out that the Power Management in the BIOS was seeming to be confused ever since I had my 9.04 upgraded to 9.10.
I disabled Wake UP On options in the BIOS, and this seems to have stopped the laptop to restarting everytime you shutdown the machine.

---

