---
title: "Battery Life Issues"
date: 2009-09-11
forum: General Help
---

### Post by mleonard2012 on 2009-09-11
i have a gateway lt3103u netbook with an amd l110 processor and x1270 graphics running ubuntu 9.04 and compiz effects with wireless working, power management now working to clock cpu down from 1.2 ghz to 800 mhz and the 3d graphics drivers that came with the ubuntu installation.  in my past experience, ubuntu has always had atleast an hour of battery life over windows vista, however when i installed ubuntu on this mahcine, it only gets 3 1/2 hours on ubuntu and 5-5 1/2 on windows when just idling (even with the cpu scaling in ubuntu)  and windows using balanced power mode with minimum display brightness.  any ideas as to why the sudden drop in battery life?

---

### Post by mleonard2012 on 2009-09-12
no ideas?

---

### Post by AutoStatic on 2009-09-18
Hello, how did you enable CPU scaling?

---

### Post by mleonard2012 on 2009-09-20
i used this guide:

[http://ubuntuforums.org/showthread.php?p=7868889](http://ubuntuforums.org/showthread.php?p=7868889)

it worked great, no hard work involved

---

### Post by AutoStatic on 2009-09-22
Used that guide too, but I get lockups every now and then.
When it comes to saving battery life, you could try **powertop**.

---

### Post by mleonard2012 on 2009-09-22
has that helped the battery life for you?  because i read somewhere that it might be the graphics driver not allowing the integrated graphics to save power.  but that may be wrong

---

### Post by AutoStatic on 2009-09-24
Yes it helped for me. Together with my custom kernel I can get power usage under 12W, so that's about 4 hours. And I think that if the graphics driver would allow the integrated graphics to save power it would be possible to get lower than 10W. But I haven't come across any article/information on the open source radeon driver and power saving settings.

---

### Post by mleonard2012 on 2009-09-24
that is about what i'm getting now, somewhere between 3 1/2 to 4 hours.  but sadly, i still need to use windows since i'm able to get up to 6 hours of web browsing from it by lowering the screen brightness.  i really wouldn't even have the technical skill to mess with the graphics driver unless someone actually made a guide.  i would really love to start using ubuntu again

---

### Post by Mimz on 2009-09-24
Could just be the battery... lol if you leave it charging for a long time sometimes it messes up the battery, and over time it will get worse. My phone used to that now I take out the charger cord everytime its finished but idk if thats whats wrong with urs

---

### Post by e24ohm on 2009-09-24
> **mleonard2012 said:**
> i have a gateway lt3103u netbook with an amd l110 processor and x1270 graphics running ubuntu 9.04 and compiz effects with wireless working, power management now working to clock cpu down from 1.2 ghz to 800 mhz and the 3d graphics drivers that came with the ubuntu installation.  in my past experience, ubuntu has always had atleast an hour of battery life over windows vista, however when i installed ubuntu on this mahcine, it only gets 3 1/2 hours on ubuntu and 5-5 1/2 on windows when just idling (even with the cpu scaling in ubuntu)  and windows using balanced power mode with minimum display brightness.  any ideas as to why the sudden drop in battery life?What version of Ubuntu did you install? I have had better luck with the "LTS" versions for battery life.

---

### Post by e24ohm on 2009-09-24
> **mleonard2012 said:**
> i used this guide:

[http://ubuntuforums.org/showthread.php?p=7868889](http://ubuntuforums.org/showthread.php?p=7868889)

it worked great, no hard work involvedGreat link, thanks for the post. I will be using this later today, to see if I can carve out more life from my battery.

cheers!!!

---

### Post by mleonard2012 on 2009-09-24
well i just got the netbook a week or two ago, so that's not it.  thanks though

---

### Post by mleonard2012 on 2009-09-24
well i believe i have tried 8.04, 8.10, and 9.04 on the netbook, and will soon upgrade to 9.10 as soon as it is released.  i believe alpha 5 of 9.10's kernel supports the same thing we did with the patch.  isn't 9.10 going to be LTS?

Edit:  I am on alpha 6 of karmic koala now, and no, it does not support frequency scaling on the processor.  but on a side note, i find it to be slightly faster and with a cleaner look in my opinion

---

### Post by AutoStatic on 2009-09-25
10.04 (Lucid Lynx) will be the new LTS version.
And what kernel version is shipped with the Karmic Koala Alpha 6 release?

---

### Post by mleonard2012 on 2009-09-25
The kernel that shipped with alpha 6 is the 2.6.31-9.29 kernel based on the 2.6.31-rc8 kernel

---

### Post by AutoStatic on 2009-09-26
That kernel does not support frequency scaling, the powernow-k8 module does not have all the necessary patches. Besides, you will need a custom DSDT that does not get loaded with the 2.6.31-rc8 kernel.

---

