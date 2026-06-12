---
title: "Random Total System Freeze, only mouse moves slowly"
date: 2009-09-28
forum: General Help
---

### Post by dudegaurav on 2009-09-28
Hi guys, 

I'm having a very frustrating problem here. 

My system (ubuntu 9.10) is freezing up completely at random times, and requires me to do a hard reboot every time. The keyboard is totally frozen, not responding to any keystrokes. The mouse pointer moves but does not click/respond. 

I have tried gnome/kde/xfce , and this problem occurs on all of them. Previously, I was on Jaunty, when this problem started occurring, so I upgraded to Karmic in hope of a fix. Sadly, it wasnt fixed. 

My system specs are in the specs.txt file attached. 

I have tried to spot the problem causing daemon/process by looking at system logs every time after a crash, but could not spot any thing consistently. 

My suspicion is on NetworkManager, however I have no proof ! 

Can anyone help me out here ? 

Thanks in advance,
Gaurav

---

### Post by FunkyRes on 2009-09-28
Open a terminal and run top.
That should show you what is eating your cycles.

I've had that happen before as a result of JavaScript related memory leak in Firefox, using noscript helps avoid the issue.

---

### Post by dudegaurav on 2009-09-28
No application necessarily is eating my cycles. I have had system freeze's with top open, but at the point of the freeze, no application reported more than 5-10% cpu or ram usage. 

Also, when the system freezes, display is unresponsive (total hang) so top does not refresh of course.

---

