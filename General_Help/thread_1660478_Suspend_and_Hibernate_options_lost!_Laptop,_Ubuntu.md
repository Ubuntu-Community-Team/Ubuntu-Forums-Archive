---
title: "Suspend and Hibernate options lost! Laptop, Ubuntu 10.10."
date: 2011-01-05
forum: General Help
---

### Post by Svens on 2011-01-05
Hi!
Strange thing happened to my Ubuntu 10.10. There are no more suspend and hibernate options. I don't know when they disappeared.
Before that I installed "laptop-mode-tools", but when I found that those two options are lost, I deleted (sudo apt-get remove) it. So I think that is not the problem.
When I close the lid of my laptop, it doesn't suspend as it should be, but it is giving me an error message:
```
Computer failed to suspend.
Failure was reported as: Cannot suspend
```
What could be the problem?
Laptop model: HP Pavilion dv6500
Thank you in advance!

P.S. I'm adding a picture with that error message.

---

### Post by Svens on 2011-01-05
Problem solved!
When you install laptop-mode-tools , it DELETES pm-utils. And pm-utils is important so laptop could suspend. So I had to reinstall by myself pm-utils (sudo apt-get install pm-utils).

BUG: [https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)

---

### Post by wintermute000 on 2011-01-09
Thanks for that. What a stupid bug. 
In fact power management in 10.10 seems kinda borked on several thinkpads I've tried it on, getting half the battey life under 8.0 or win7 / winxp.

---

### Post by honus100 on 2011-05-14
Thanks for the solution, I was at the point of reinstalling if I didn't find a fix. I had done the same thing, installed laptop-mode-tools, killed suspend ability.

---

### Post by kedmond on 2011-06-22
Thank you so much for that fix!

---

