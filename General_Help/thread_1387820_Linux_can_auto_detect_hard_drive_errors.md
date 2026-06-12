---
title: "Linux can auto detect hard drive errors?"
date: 2010-01-22
forum: General Help
---

### Post by Roasted on 2010-01-22
Someone explain this to me. I often thought in the back of my head, how do I check if my drive is bad in Linux? I always excused it thinking well I guess besides gaming that's another reason to keep a windows partition around.

I boot up yesterday and Gnome was acting weird. Then, it happened. "We have detected bad sectors in your hard drive." 

I thought, no, you're stupid, this hard drive is less than a year old (however it was a replacement for another one that died). So I reboot.

Boot back up - Different error message. But instead of getting it a few minutes after log in, I got it right away. "We have detected potential hard drive failure."

Okay, Linux. Want to play this game? Booted to Vista, downloaded Seatools to test my Seagate drive. It failed... Swapped SATA cables... it failed...

So I ask - how does Linux have this auto detect capability like that? As much as I love Ubuntu, I was like there's no way it could just magically tell like that without running the Seagate program. But alas, Ubuntu was dead on target.

How's this work? How accurate is it?

---

### Post by lotharmat on 2010-01-22
It reads the S.M.A.R.T. data

---

### Post by Roasted on 2010-01-22
> **lotharmat said:**
> It reads the S.M.A.R.T. data

How definitive is that, in comparison to the long DPS test or whatever you can use through the Seatools program?

Does Windows read the SMART data?

---

### Post by doas777 on 2010-01-22
it's as accurate as your hdd firmware can make it.
SMART is somthing that your hdd firmware handles, storing/accumulating performance metrics. ubuntu and windows just read the smart data off the drive controller, and echo it to the user, sometimes with some useful interpretation/analysis. 

my advise is, if you care for your data, take SMART warnings very seriously. they're the only warnings you're gonna get.

---

### Post by Roasted on 2010-01-22
> **doas777 said:**
> it's as accurate as your hdd firmware can make it.
SMART is somthing that your hdd firmware handles, storing/accumulating performance metrics. ubuntu and windows just read the smart data off the drive controller, and echo it to the user, sometimes with some useful interpretation/analysis. 

my advise is, if you care for your data, take SMART warnings very seriously. they're the only warnings you're gonna get.

Well, I do nightly backups of my system (thank you rsync + crontab). But I just didn't understand why Linux told me I had an error but Windows did not.

---

### Post by oldfred on 2010-01-22
From synaptic download
GSmartControl is a graphical user interface for smartctl, which is a tool for
querying and controlling SMART (Self-Monitoring, Analysis, and Reporting
Technology) data on modern hard disk drives.

I believe their are also windows tools for this as it is a standard for hard drives.
[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

---

### Post by doas777 on 2010-01-22
> **Roasted said:**
> How definitive is that, in comparison to the long DPS test or whatever you can use through the Seatools program?

Does Windows read the SMART data?

smart is a bit differant from dps testing, in that it is just a set of stats. when the drive powers up, it increments the load_cycle_count, and Powered_on_hours_count, etc. if the drive encounters an error, it records that an error occured. however a bad block that is in freespace will never be accessed so it won't be noticed or recorded by SMART.

the DPS test, will actually check for bad blocks, and other surface and filesystem anomalies, in addition to performing an analysis of the SMART stats.

---

### Post by doas777 on 2010-01-22
> **Roasted said:**
> Well, I do nightly backups of my system (thank you rsync + crontab). But I just didn't understand why Linux told me I had an error but Windows did not.
if windows tells you, it will be in the system log, until the issue becomes so severe that the drive starts to appear and disappear.
you can install speedfan for windows, which has an interface for analyzing SMART data. check and see how it looks.

---

### Post by Roasted on 2010-01-22
Is this just another -1 for Windows, then? I was just surprised Linux was the one to notify me of the error, meanwhile Vista never told me of the error, despite it also acting weird.

---

### Post by muteXe on 2010-01-22
> **lotharmat said:**
> It reads the S.M.A.R.T. data

Great explanation....

---

