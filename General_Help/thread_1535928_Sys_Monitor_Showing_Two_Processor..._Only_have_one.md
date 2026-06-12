---
title: "Sys Monitor Showing Two Processor... Only have one"
date: 2010-07-21
forum: General Help
---

### Post by Shane.Hughes on 2010-07-21
I am running a Dell client at work with Ubuntu 9.10, Kernel is 2.6.31-22 -generic. Hardware info for the client is [here.](http://support.dell.com/support/topics/global.aspx/support/my_systems_info/details?c=us&cs=19&l=en&s=biz&~ck=anavml&~tab=2)

I was reading the [Picking the Kernel That's Right for You Guide](http://ubuntuforums.org/showthread.php?t=85917) and check System Monitor to see if the client had dual core or not and there it states that I am running two 2.8Ghz proccessors under the System Tab and shows two processors under the Resources Tab as well.

Why/How is this happening? Any input would be appreciated. I am pretty new to Linux, so I apologize if this is a really noob question or if it belonged somewhere else/was already posted (I didn't see it).
[]("http://support.dell.com/support/topics/global.aspx/support/my_systems_info/details?c=us&cs=19&l=en&s=biz&%7Eck=anavml&%7Etab=2")

---

### Post by RJARRRPCGP on 2010-07-21
Probably because it's a Pentium 4 with hyper threading.

---

### Post by Shane.Hughes on 2010-07-21
That though had occurred to me, but Hyperthreading isn't another processor, it just sometimes acts like another one IF the program(s) you are using support it. Should that really show two? And I have a quadcore at home that I was thinking of installing Ubuntu on, cause it's great, but it has hyperthreading support. Does that mean System Monitoring will show 8 processors?

---

### Post by LowSky on 2010-07-21
> **Shane.Hughes said:**
> That though had occurred to me, but Hyperthreading isn't another processor, it just sometimes acts like another one IF the program(s) you are using support it. Should that really show two? And I have a quadcore at home that I was thinking of installing Ubuntu on, cause it's great, but it has hyperthreading support. Does that mean System Monitoring will show 8 processors?
I dont really see the problem?

---

### Post by kaelspencer on 2010-07-21
What happens is the kernel addresses two virtual processors for each physical core when the CPU has hyper-threading. Thus, you see two cores in system monitor.

See the [Wikipedia article]("http://en.wikipedia.org/wiki/Hyper-threading").

---

### Post by cliffdodger on 2010-07-21
Yes. I remember a colleague I worked with running Linux on P4 hyperthreaded cpu's years back when they first came out and they always showed up as two cpu's. If you have a quad core with hyperthreading you should see 8 cpu's under linux. ~edit~ what kaelspencer said.  I was afk and didn't see your reply before posting.

---

