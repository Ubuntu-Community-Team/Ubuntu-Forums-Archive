---
title: "Disable Package Update Reminders"
date: 2012-05-07
forum: General Help
---

### Post by jgooch on 2012-05-07
Since I have a number of applications installed that depend on modules compiled for my specific kernal, I need a bit more control over when and what gets updated. 

The nagging popup reminders for update often lead me to just click "ok" to get them out of my way so that I can go back to what I was doing (coding, troubleshooting, etc ) 

Today I had no less than 3 hours of application downtime because the updates updated the kernel and prevented my apps from running. 

What I'd like to do, but could not find via forum search, is a way to disable these nagging pop-ups and reminders that come up when I ssh into my Ubuntun 12.04 box. I'd rather have the system not bug me as I have a standard routing of backing up the system periodically before applying updates. This lets me restore the system quickly of I discover an update has broken something important.


Thanks for reading this far.

If you know how to disable the reminders, I will be in your debt.

---

### Post by zvacet on 2012-05-08
You can do it in synaptic when you will pick apps you don't want to be updated and under package tab click  lock version.After that you will not get updates for these apps.For doing same thing from terminal see [this.]("http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html")

---

### Post by grahammechanical on 2012-05-08
I can run the Update Manager and change the settings so that it automatically checks for updates

Daily
Every two days
weekly
Every fortnight
Never

This is not new to 12.04. I used this with 7.04 when I was on dial-up and pay by the minute. It gave me manual control over when I did updates by clicking Check.

Regards.

---

### Post by zvacet on 2012-05-08
You can use option witch **grahammechanical** adviced,but in that case you will not get any updates.That includes security updates too.It is up to you,but I will try option I suggested.

---

