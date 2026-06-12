---
title: "Scheduled wake-up and shutdown of system"
date: 2009-10-13
forum: General Help
---

### Post by praveenthivari on 2009-10-13
Hi,
    I am using ubuntu jaunty jackalope and have to download between 2 at night and 8 in the morning. So I need a program which can enable my system to wake up and shutdown between these times. 
I searched for this on the forum for threads relating to this and got some results to 'Handle BIOS', which i am a bit afraid to do, so if anyone could help me with software to do it would be great.

And one more thing, when i wake my system from hibernation it is in 'Locked' state for which I need to give password and then enter. Can I disable this feature?

---

### Post by P4man on 2009-10-13
Your first question, Im anxious to see an answer, as ive been struggeling with that for ages. I haven't found an easy solution yet :(

THe second question is easy. open gconf-editor. Browse to apps > gnome-power-manager > lock. Uncheck hibernate.

---

### Post by mcduck on 2009-10-13
Sorry, but if your BIOS doesn't have such feature your are out of luck. No software will help you there, since no software is running when the computer is shut down...

---

### Post by P4man on 2009-10-13
> **mcduck said:**
> Sorry, but if your BIOS doesn't have such feature your are out of luck. No software will help you there, since no software is running when the computer is shut down...

No, but software could set the acpi wake up time. Its certainly possible. For instance, I ran a suspend/resume test script for jaunty ([https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)), and it would put the machine to sleep, and set it to wake up x seconds or  minutes later. Worked fine. All I need is an interface to set that x minutes :)

edit: have a look here:
[http://www.mythtv.org/wiki/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm](http://www.mythtv.org/wiki/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm)

Its not exactly a shiny GUI, but it might work.

---

### Post by praveenthivari on 2009-10-13
> **mcduck said:**
> Sorry, but if your BIOS doesn't have such feature your are out of luck. No software will help you there, since no software is running when the computer is shut down...


I don't know whether I have that feature or not. It's a new system so it may be there. But the thing is I dont want to mess with BIOS. 

I was just thinking of a simple direct solution just as we have a built in time scheduler in windows operating systems:P

---

### Post by mcduck on 2009-10-13
Well, Linux has a built-in scheduler as well (Cron). But what you want to do  still depends on your BIOS having that feature, and actually handling the scheduling, as like I said no software is running when the computer is shut down. And that would of course include your operating system and all it's features.

---

### Post by P4man on 2009-10-13
Just about every machine that is less than 6-7 years old should support ACPI wakeup. In the link I posted it is explained how to check it. Its definitely possible, even fairly easy, I just haven't come across a GUI to make use of it. Perhaps I should teach myself python and make something. Check back here in hmm.. 2 years or so :p

---

### Post by praveenthivari on 2009-10-13
> **P4man said:**
> Just about every machine that is less than 6-7 years old should support ACPI wakeup. In the link I posted it is explained how to check it. Its definitely possible, even fairly easy, I just haven't come across a GUI to make use of it. Perhaps I should teach myself python and make something. Check back here in hmm.. 2 years or so :p


I'll ckeck the link and report back.
Well certainly I'll be looking forward for that kind of software.:P:P:P:P

I just wonder why is it so difficult to create a simple ,easy to run soft on linux which is done so easily on Windows system. Is it that difficult???

But anyway thanks for ur replies

---

### Post by mcduck on 2009-10-13
> **praveenthivari said:**
> I'll ckeck the link and report back.
Well certainly I'll be looking forward for that kind of software.:P:P:P:P

I just wonder why is it so difficult to create a simple ,easy to run soft on linux which is done so easily on Windows system. Is it that difficult???

But anyway thanks for ur replies

What makes you think it's *difficult* to create such software?

It's more a question of if there is anybody who a) wants such software, b) has basic programming skills and c) has enough time to do it. Or somebody who want s such software enough to be ready to pay somebody to create it.

During the years I've spent on these forums you are the first person I've seen to ask for such feature. :)

Based on the information P4man posted above it seems that a simple GUI for the purpose could be easily created even with a shell script.

---

### Post by P4man on 2009-10-13
> **praveenthivari said:**
> I'll ckeck the link and report back.
Well certainly I'll be looking forward for that kind of software.:P:P:P:P

I just wonder why is it so difficult to create a simple ,easy to run soft on linux which is done so easily on Windows system. Is it that difficult???

But anyway thanks for ur replies

Programming for linux isnt any harder than for windows. Its just that window has such a large marketshare, its kinda logical you'll find more programs for it. Not necessarily *better *programs (although, in some cases that too), but certainly more. 

Also, given linux history and prior "target market", a lot of things work on a terminal, and no one ever bothered to make a gui for it. 

last reason perhaps is the fragmentation of the linux market. Its already relatively small, and then half the people use gnome, others KDE, XFCE, and what not. And then you got package management that differs from distro to distro, and I guess in a way, it IS harder to make a linux app, at least if you want it to be fairly universal.

Anyway, don't hold your breath for me making this, I haven't programmed in like 10 years, and I just started reading a Python book.. you know, diagonically. This might be a good training project though, its gotta be dead easy once I get beyond the basics of the syntax and building a GUI :)

---

### Post by praveenthivari on 2009-10-14
> **mcduck said:**
> What makes you think it's *difficult* to create such software?

It's more a question of if there is anybody who a) wants such software, b) has basic programming skills and c) has enough time to do it. Or somebody who want s such software enough to be ready to pay somebody to create it.

During the years I've spent on these forums you are the first person I've seen to ask for such feature. :)

Based on the information P4man posted above it seems that a simple GUI for the purpose could be easily created even with a shell script.


I asked because I see that all softwares we use in ubuntu are free. And I thought that to create a GUI app for ' auto wake up' wouldn't take more than 2-3 Mb. And there are many threads on this forum and others regarding it. So, even after that none has come up with some app. That's why I thought that may it was difficult to create a app.

l am learning basics of CLI so in time I may know how to work effortlessly with it.:P:P:P:P

---

### Post by praveenthivari on 2009-10-14
> **P4man said:**
> Programming for linux isnt any harder than for windows. Its just that window has such a large marketshare, its kinda logical you'll find more programs for it. Not necessarily *better *programs (although, in some cases that too), but certainly more. 

Also, given linux history and prior "target market", a lot of things work on a terminal, and no one ever bothered to make a gui for it. 

last reason perhaps is the fragmentation of the linux market. Its already relatively small, and then half the people use gnome, others KDE, XFCE, and what not. And then you got package management that differs from distro to distro, and I guess in a way, it IS harder to make a linux app, at least if you want it to be fairly universal.

Anyway, don't hold your breath for me making this, I haven't programmed in like 10 years, and I just started reading a Python book.. you know, diagonically. This might be a good training project though, its gotta be dead easy once I get beyond the basics of the syntax and building a GUI :)

You rightly said my point that Linux community is fragmented within itself. 
May be it is only for better for Linux itself or otherwise we wouldn't get so many flavours from the same source

---

### Post by brijith on 2009-10-14
> **P4man said:**
> 


[http://www.mythtv.org/wiki/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm](http://www.mythtv.org/wiki/ACPI_Wakeup#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm)

Its not exactly a shiny GUI, but it might work.


Great !!!! It worked for me :)

---

### Post by praveenthivari on 2009-10-14
> **brijith said:**
> Great !!!! It worked for me :)

Thanks

---

