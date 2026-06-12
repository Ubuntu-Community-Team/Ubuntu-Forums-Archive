---
title: "Ubuntu insists my battery is about to die"
date: 2011-02-22
forum: General Help
---

### Post by RobotGymnast on 2011-02-22
I have a Dell Vostro 1510 laptop, with the extended battery. The battery's been worn down, though, and Ubuntu warns me that my battery life sucks. I can deal with this. The problem is that when I unplug the computer (no matter the charge level), Ubuntu insists my battery is about to turn critical, and hibernates. If I start up the computer on battery life, everything works fine, but starting the computer on AC and unplugging it causes the computer to hibernate. It's very annoying.

Any help? Is there an extended power management package I can get?

---

### Post by jbbeach710 on 2011-03-05
I'm experiencing a somewhat similar problem.  Hopefully somebody who can help will see this thread.

I bought a Dell Vostro 1500 laptop in October 2007 with the extended capacity battery.  At first I only had Windows XP on the computer, and the battery lasted as long as >7 hours between charges, which was its advertised capacity.  I continued to experience this level of performance right up until I wiped the hard drive clean and switched to Ubuntu in November 2009.  The first time I booted Ubuntu after installing it I got a message that said something like "your battery has a very low capacity and may be broken", and I've been getting this message ever since.  I've tried letting it run all the way down and charging the battery with power off, but that hasn't helped.  When I open the "device information" window after letting it charge for a long time, it will tell me that the battery is 100% charged but the capacity is 27.5%.  I really don't think the battery broke during the couple hours that I spent switching operating systems, so I'm pretty sure it's a Ubuntu issue.  Does anybody have any ideas about what could be wrong or how to fix it?

---

### Post by RobotGymnast on 2011-03-05
> **jbbeach710 said:**
> I'm experiencing a somewhat similar problem.  Hopefully somebody who can help will see this thread.

I bought a Dell Vostro 1500 laptop in October 2007 with the extended capacity battery.  At first I only had Windows XP on the computer, and the battery lasted as long as >7 hours between charges, which was its advertised capacity.  I continued to experience this level of performance right up until I wiped the hard drive clean and switched to Ubuntu in November 2009.  The first time I booted Ubuntu after installing it I got a message that said something like "your battery has a very low capacity and may be broken", and I've been getting this message ever since.  I've tried letting it run all the way down and charging the battery with power off, but that hasn't helped.  When I open the "device information" window after letting it charge for a long time, it will tell me that the battery is 100% charged but the capacity is 27.5%.  I really don't think the battery broke during the couple hours that I spent switching operating systems, so I'm pretty sure it's a Ubuntu issue.  Does anybody have any ideas about what could be wrong or how to fix it?

Uh-oh. My battery's the extended on a Dell Vostro 1510. Not boding well.

---

### Post by seawolf167 on 2011-03-05
I suspect this is because of the battery being too old. Batteries are considered "consumables" and that's the reason they have very limited warranties. I had this issue with a similar laptop (1510 I think) at work and a replacement battery fixed the problem.

My suspicion is that your old battery is misreporting it's charge level, then Ubuntu thinks the battery is going to die and thus hibernates. 

If this is the case, the solution would be to turn off hibernation, set it to hibernate after a longer period of time, or replace the battery.

---

### Post by StephenDavison on 2011-03-05
I think you're experiencing this known bug:
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190")

It happens all the time on my netbook if I don't suspend before unplugging the cord.

---

### Post by RobotGymnast on 2011-03-06
> **StephenDavison said:**
> I think you're experiencing this known bug:
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190")

It happens all the time on my netbook if I don't suspend before unplugging the cord.

Great, thank you!

---

