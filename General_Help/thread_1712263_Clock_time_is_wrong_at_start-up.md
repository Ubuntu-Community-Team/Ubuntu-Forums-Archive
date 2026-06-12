---
title: "Clock time is wrong at start-up"
date: 2011-03-22
forum: General Help
---

### Post by kbon on 2011-03-22
Pretty much what the title says. Everytime I reboot Ubuntu,the clock is behind by two hours and needs to be manually set. Is there a way to fix this?

---

### Post by 5149.5 on 2011-03-22
It sounds like your time zone is not set correctly. Click the clock, when it opens, click location, and then click edit. Make sure that is correct.

---

### Post by matt_symes on 2011-03-22
Hi

Are you dual booting with windows ?

Kind regards

---

### Post by kbon on 2011-03-22
Thanks! That fixed it.
Edit: Yes I am dual booting.

---

### Post by matt_symes on 2011-03-22
Hi

> Edit: Yes I am dual booting.

Make sure Ubuntu is set to local time and not UTC.

Kind regards

---

### Post by kbon on 2011-03-22
I rebooted with the time zone set and still get the wrong time...
Do I have to go into Windows and set something?...

---

### Post by 5149.5 on 2011-03-22
> **kbon said:**
> I rebooted with the time zone set and still get the wrong time...
Do I have to go into Windows and set something?...

Your clock on the mother board must be off.

---

### Post by kbon on 2011-03-22
Hrm... any idea on how to set that?

---

### Post by 5149.5 on 2011-03-22
> **kbon said:**
> Hrm... any idea on how to set that?

You have to get into the BIOS settings and that varies by manufacturer. There should be a  brief message about pressing a function key at the very beginning of the boot process. You have to be quick or it will continue past that and there is no going back. On some machines the best way is to hold down that function key while turning on power.

---

### Post by kbon on 2011-03-22
Checked that, the settings are fine... And it still doesn't set the clock right.

---

### Post by 5149.5 on 2011-03-22
> **kbon said:**
> Checked that, the settings are fine... And it still doesn't set the clock right.

I have no idea then.

---

### Post by wojox on 2011-03-22
Try setting your ntp settings in date and time.

---

### Post by valueshop95 on 2011-03-22
Try to change CMOS battery.

---

### Post by 5149.5 on 2011-03-22
> **wojox said:**
> Try setting your ntp settings in date and time.

I thought about suggesting that, but will it make a 2 hour correction? I might be wrong, but I thought NTP made small adjustments.

---

### Post by wojox on 2011-03-22
> **5149.5 said:**
> I thought about suggesting that, but will it make a 2 hour correction? I might be wrong, but I thought NTP made small adjustments.

I forget. I thought I had this problem with Fedora/Vista and that fixed it. :P

---

### Post by 5149.5 on 2011-03-22
> **wojox said:**
> I forget. I thought I had this problem with Fedora/Vista and that fixed it. :P

You're probably right. I was curious and googled ntp protocol just now. The packet includes a date and time which I assume is UTC. That should straighten out a clock no matter the difference as long as it's time zone is set correctly.

---

### Post by matt_symes on 2011-03-22
Hi

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

Read the section Multiple Boot Systems Time Conflicts.

Maybe that's the issue ?

Kind regards

---

### Post by kbon on 2011-03-23
I fixed the clock issue by clicking the clock, bringing up the calender, then clicking the locations tab and clicking the set button by the bottom of the timezone. Thanks for the help!

---

