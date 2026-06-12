---
title: "How do I reset S.M.A.R.T status of a drive?"
date: 2010-11-08
forum: General Help
---

### Post by ubnewbie2 on 2010-11-08
I have a report appearing in Ubuntu 10.04 LTS (and by the BIOS at boot time) about one of my drives.   

It is an old PATA drive that is non-critical. It says disk failure is imminent, and finds 113 bad sectors.  Basically it has had some write errors and relocated some sectors.   I want to keep using it - nothing important on it that I don't have copies of elsewhere.

There number of errors is not increasing. I'd like to just watch it and see if more errors occur. Is there a way to reset the alarm so it doesn't nag me until it happens again.

---

### Post by krupintupple on 2010-11-08
a reply to the above also interests me. :)

---

### Post by endotherm on 2010-11-08
It is my understanding that you cannot clear the stats, save by replacing the controller circuitry on the bottom of the HDD. perhaps attacking the software firing the alarm is the best bet.

hope you get it worked out

---

### Post by searchfgold6789 on 2010-11-08
I would say, no.

---

### Post by ubnewbie2 on 2010-11-08
> **endotherm said:**
> It is my understanding that you cannot clear the stats, save by replacing the controller circuitry on the bottom of the HDD. perhaps attacking the software firing the alarm is the best bet.

hope you get it worked out


Since the BIOS is causing it to halt at boot time until I respond, I would need to have a look there as well.  I will see if SMART checking can be turned off on an individual basis in the BIOS.  

Meanwhile the software reporting it under Ubuntu seems to be part of the gnome desktop, installed by default.  It appears in the system tray and when you click on the alarm, it launches something called Disk Utility 2.30.1 (copyright Redhat).  Is there any way to configure that?

---

### Post by ubnewbie2 on 2010-11-08
I also wanted to add that I never had any problems until recently when I turned on the automatic suspend feature to save some power when I was away from the computer.  After a week of auto-suspending, I now get this error.  Just coincidence or does suspend do nasties to hard drives sometimes?

---

### Post by dcstar on 2010-11-09
> **ubnewbie2 said:**
> I have a report appearing in Ubuntu 10.04 LTS (and by the BIOS at boot time) about one of my drives.   

It is an old PATA drive that is non-critical. It says disk failure is imminent, and finds 113 bad sectors.  Basically it has had some write errors and relocated some sectors.   I want to keep using it - nothing important on it that I don't have copies of elsewhere.

There number of errors is not increasing. I'd like to just watch it and see if more errors occur. Is there a way to reset the alarm so it doesn't nag me until it happens again.

Go into the Disk Manager and select "Don't warn me if the disk is failing" in SMART.

---

### Post by cbhargava on 2010-11-09
> **ubnewbie2 said:**
> I have a report appearing in Ubuntu 10.04 LTS (and by the BIOS at boot time) about one of my drives.   

It is an old PATA drive that is non-critical. It says disk failure is imminent, and finds 113 bad sectors.  Basically it has had some write errors and relocated some sectors.   I want to keep using it - nothing important on it that I don't have copies of elsewhere.

There number of errors is not increasing. I'd like to just watch it and see if more errors occur. Is there a way to reset the alarm so it doesn't nag me until it happens again.

Once SMART gets tripped it can not be reset by the end user. SMART is a preemptive indication of a mechanical failure. Check if the drive is in warranty. Get it replaced anyways as it is not worth (time & efforts) to store data on that drive.

---

### Post by dcstar on 2010-11-09
***It is an old PATA drive that is non-critical***
> **cbhargava said:**
> Check if the drive is in warranty. Get it replaced anyways as it is not worth (time & efforts) to store data on that drive.

---

### Post by ubnewbie2 on 2010-11-09
> **dcstar said:**
> Go into the Disk Manager and select "Don't warn me if the disk is failing" in SMART.


Thank you.  I had missed that check box stuck down at the bottom of the window.  That has stopped it complaining.

---

### Post by ubnewbie2 on 2010-11-09
> **dcstar said:**
> ***It is an old PATA drive that is non-critical***

Yes exactly :)  

I will just use it as a scratch area.  As the errors are not increasing it might be fine for some time yet.  But any more trouble and I will bin it.

---

### Post by psusi on 2010-11-09
> **ubnewbie2 said:**
> Yes exactly :)  

I will just use it as a scratch area.  As the errors are not increasing it might be fine for some time yet.  But any more trouble and I will bin it.

Unless you regularly run the long smart self test, the error count will not increase unless you happen to try reading the bad part of the disk, which if you aren't using it much, can allow the growing problem to remain hidden for some time.

---

