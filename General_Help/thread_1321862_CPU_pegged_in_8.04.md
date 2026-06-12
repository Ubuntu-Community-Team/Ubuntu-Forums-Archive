---
title: "CPU pegged in 8.04"
date: 2009-11-10
forum: General Help
---

### Post by Bunny Boy on 2009-11-10
I'm running Hardy Heron on a Compaq Evo N800c.

Heres the systeminfo:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz
stepping	: 7
cpu MHz		: 2000.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no

My problem is that I get very slow performance, particularly while web browsing with either Firefox, Seamonkey, or Opera. (it is the slowest with the last one) When I check the system monitor, the graph shows that my CPU usage is hovering around 100%.  

Checking the system monitor before I launch a browser typically shows the CPU around 40%, but it jumps up around 80% when I make the system monitor the active window!

Any clues as to why a 2 GHz P4 should be performing so poorly with Hardy?

PS When I check the process list in System Monitor, I can't see anything that is hogging the CPU (yes, I have show all checked)

---

### Post by hwttdz on 2009-11-10
Try using top at the command line, and see what process is taking up all the cpu there.

---

### Post by Bunny Boy on 2009-11-10
> **hwttdz said:**
> Try using top at the command line, and see what process is taking up all the cpu there.

Well, that's interesting.  top shows that Xorg tends to hog the most CPU, sometimes going as high as 63%, but system monitor never shows it going above 15%.

Is the X server really such a resource hog?

---

### Post by XCan on 2009-11-11
No it shouldn't. It usually only does that when there's some issue with the graphics drivers. Is there any reason you're running such an old version of Ubuntu?

---

### Post by Bunny Boy on 2009-11-11
> **XCan said:**
> No it shouldn't. It usually only does that when there's some issue with the graphics drivers. Is there any reason you're running such an old version of Ubuntu?

Well, it was the latest when I got that laptop about a year ago, and my experience with upgrading Ubuntu has been abysmal.

---

### Post by XCan on 2009-11-12
Have you had this issue since the beginning then, or has it just recently popped up?

I have not had any issues with upgrading so far. And honestly, you should really upgrade, at least to 8.04 LTS. 6.06's support ended July 14, 2009, so you won't even be getting any security patches.

---

### Post by Bunny Boy on 2009-11-12
> **XCan said:**
> Have you had this issue since the beginning then, or has it just recently popped up?

I have not had any issues with upgrading so far. And honestly, you should really upgrade, at least to 8.04 LTS. 6.06's support ended July 14, 2009, so you won't even be getting any security patches.

As stated earlier in the thread, and the subject heading! the laptop in question is running 8.04.  You must be confused, XCan, about my signature, which contains the stats for the desktop computer that I've been running with 6.06.

Anyway, yes, this problem has been happening since I installed 8.04 a little over a year ago. I didn't worry about it too much because I was mostly using this laptop for accounting and it wasn't an issue.  I've got it connected to the internet now, though, and find that any website with a javascript totally bogs it down.

---

### Post by XCan on 2009-11-13
Confused indeed. ;) It even says dapper in your profile. :p

---

