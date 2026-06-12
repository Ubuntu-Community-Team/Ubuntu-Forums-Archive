---
title: "Ubuntu 11.10 - Performance issues after upgrade"
date: 2011-11-27
forum: General Help
---

### Post by alexei_ on 2011-11-27
Have recently upgraded to Ubuntu 11.10.
After fresh reboot it working kind of OK -- I have 2 web browsers with about 20 windows in each + byoby with vim.

My laptop has "AMD Athlon II X2 M300" with 4Gb DDR2 of RAM.
However after returning back from "Standby" the issues start happening.
 I have time with with seconds -- it is freezing... eating 3-10 seconds.
 When I do "Ctrl+Tab" I have to wait 3-10 seconds to get any action.
 Similarly behaves all other soft.

htop shows less then 50% of any of CPUs usage.
Memory usage is about 2700 out of 3700. Swap usage is about 1200 out of 10000.

Why this is happening?
Last time when I tried to reboot -- that did not happen in 20 minutes -- I had to do power reset.

---

### Post by oldtimer7777 on 2011-11-27
Perhaps, but I am not sure, it could be that you have 20 windows open in each? 

Did this kind of strange behavior happen before in Ubuntu 11.04 or any of the other flavor of Ubuntu??   

Why do you have 20 windows open in each? 

No wonder your system is swamped. 

It is computer, not the incredible hulk. Get realistic. 

> **alexei_ said:**
> Have recently upgraded to Ubuntu 11.10.
After fresh reboot it working kind of OK -- I have 2 web browsers with about 20 windows in each + byoby with vim.

My laptop has "AMD Athlon II X2 M300" with 4Gb DDR2 of RAM.
However after returning back from "Standby" the issues start happening.
 I have time with with seconds -- it is freezing... eating 3-10 seconds.
 When I do "Ctrl+Tab" I have to wait 3-10 seconds to get any action.
 Similarly behaves all other soft.

htop shows less then 50% of any of CPUs usage.
Memory usage is about 2700 out of 3700. Swap usage is about 1200 out of 10000.

Why this is happening?
Last time when I tried to reboot -- that did not happen in 20 minutes -- I had to do power reset.

---

### Post by alexei_ on 2011-11-27
oldtimer7777, somehow Windows XP Home on 5+ years old computer (1Gb of RAM) was able to handle 40 browser windows, but Ubuntu 11.10 on dual-core with 4GB of RAM is not capable after standby?

Again, to me the issue looks to be specific to standby.

---

### Post by oldtimer7777 on 2011-11-27
> **alexei_ said:**
> oldtimer7777, somehow Windows XP Home on 5+ years old computer (1Gb of RAM) was able to handle 40 browser windows, but Ubuntu 11.10 on dual-core with 4GB of RAM is not capable after standby?

Again, to me the issue looks to be specific to standby.

We just went over this with someone else here in this forum.  I'm saying to you, having that many windows open at the same time in a Linux Ubuntu browser is going to be slow. You either don't want to accept that, or you want to be running windows.  Or you going to have to buy a solid state hard drive that can spin faster to move that cache better.  Which is it going to be? Well, that is up to you, isn't it?

---

### Post by ExemplarUbuntu on 2011-11-27
My mother hasn't had a fully working Skype in Ubuntu for well over a year. In desperation I tried yet another update.

Oh dear oh dear.

11.10 is very flaky, applications freeze or exit without warning. It locks up and is generally very, very slow even with 2-3 windows open.

I didn't even get as far as reinstalling the home folder and usual apps, it just wasn't usable.

I have now downgraded to Heron which I think was the last version that could Skype fully in both directions. I was astonished to find that the resolution issues in that LTS version have not been resolved. I am trying to remember what the fix was. I think I had to hack the xorg.conf file.

I managed to get the 1440x900 option available in the res setter dialogue but every reboot it reverts to 800x600 so there must be a default that is not being saved.

---

### Post by oldtimer7777 on 2011-11-27
Shucks, don't feel bad.  I'm in the same boat as you are right. I'm back here at 11.04 because 11.10 is having so many issues for me too. As tempting as that little "upgrade" button is sometimes, it is better not to push it unless you are willing to accept a certain amount of headache involved in that kind of decision.

> **ExemplarUbuntu said:**
> My mother hasn't had a fully working Skype in Ubuntu for well over a year. In desperation I tried yet another update.

Oh dear oh dear.

11.10 is very flaky, applications freeze or exit without warning. It locks up and is generally very, very slow even with 2-3 windows open.

I didn't even get as far as reinstalling the home folder and usual apps, it just wasn't usable.

I have now downgraded to Heron which I think was the last version that could Skype fully in both directions. I was astonished to find that the resolution issues in that LTS version have not been resolved. I am trying to remember what the fix was. I think I had to hack the xorg.conf file.

I managed to get the 1440x900 option available in the res setter dialogue but every reboot it reverts to 800x600 so there must be a default that is not being saved.

---

