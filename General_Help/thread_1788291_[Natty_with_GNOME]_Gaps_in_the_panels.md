---
title: "[Natty with GNOME] Gaps in the panels"
date: 2011-06-22
forum: General Help
---

### Post by PCaddicted on 2011-06-22
I've upgraded to Ubuntu 11.04 Natty Narwhal and I'm using GNOME classic instead of Unity.
Here's my problem:
Sometimes, I see gaps in the panels. Portions of the background picture can be seen trough them. These gaps are usually temporary. Right now I can't provide you with a screenshot of such a gap (I haven't made a screenshot).
What could be the cause?

---

### Post by PCaddicted on 2011-06-24
A gap will disappear if a right-click menu covers it.

---

### Post by PCaddicted on 2011-06-28
bump

---

### Post by aeiah on 2011-06-28
what graphics card / drivers are you using? are you using metacity or compiz with your classic gnome desktop?

---

### Post by PCaddicted on 2011-07-19
Alright, time to revive this thread :). Almost forgot about it.

I use metacity. 
Graphics card: Gigabyte ATI Radeon HD 4650, with 1GB GDDR2 graphic memory and 128 bit bandwidth  
CPU: Intel Pentium Dual Core E5200, 2,5 Ghz.

---

### Post by roololing on 2011-07-19
I had this problem before with Gnome. The right-clicks got rid of my gaps, too. If I remember correctly, I was using Compiz. I never figured out a permanent solution, but logging off and back on always worked. The gaps would eventually come back, though.

---

### Post by PCaddicted on 2011-07-20
So, does anyone know the cause and how to get this problem solved permanently?
EDIT: I've noticed that the gaps in the panels will disappear temporarily if I simply right click the panel and select one of the options in the menu (preferably "About panels"). Then, all I have to do is just close the window that appears(if I want).

---

### Post by MARP1961 on 2011-07-20
I don't know why this happens; but I do know Linux Mint 11 also seems to display the same problem from time to time. Try the following code in Terminal.
```
killall gnome-panel
``` 
This also fixes other strange broken panel icon events.

---

### Post by PCaddicted on 2011-07-24
> **MARP1961 said:**
> I don't know why this happens; but I do know Linux Mint 11 also seems to display the same problem from time to time. Try the following code in Terminal.
```
killall gnome-panel
```This also fixes other strange broken panel icon events.
This seems to only temporarily fix the problem, but a permanent or long-term solution is needed...

---

### Post by PCaddicted on 2011-07-29
Any idea?

---

