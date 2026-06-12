---
title: "How to test mdadm monitoring"
date: 2009-12-16
forum: General Help
---

### Post by the real omni on 2009-12-16
Hi,

I've set up an md raid device at /md0 and it's working great.

I've also set up mdadm to monitor the array and alert me upon any disk error or failure.

I'd like to check to ensure the monitor/alert configuration is working. Is there any way to "break" my drive array so as to trigger mdadm to send an alert?

Thanks in advance!

---

### Post by Nullexe on 2009-12-16
I've always found the best way to simulate a failure is to just pull the drive out.  

/var/log/messages should throw a lot of errors.  If you want a more detailed test procedure take a look at 

[http://tldp.org/HOWTO/Software-RAID-HOWTO-6.html](http://tldp.org/HOWTO/Software-RAID-HOWTO-6.html)

On a side-note what type of RAID are you running?

---

### Post by the real omni on 2009-12-16
> **Nullexe said:**
> I've always found the best way to simulate a failure is to just pull the drive out.  

/var/log/messages should throw a lot of errors.  If you want a more detailed test procedure take a look at 

[http://tldp.org/HOWTO/Software-RAID-HOWTO-6.html](http://tldp.org/HOWTO/Software-RAID-HOWTO-6.html)

On a side-note what type of RAID are you running?

Thanks Nullexe, the system is running RAID1 (simple mirror) so pulling the drive should be safe, it's just a bit of a pain to get at the physical machine to open it and yank the drive out, I was hoping there'd be something I could do via command line. I tried just moving /dev/md0 to /dev/md0_moved but that didn't produce any errors.

---

### Post by Nullexe on 2009-12-17
The link I posted should be able to show you how to fail the drive manually without physically unplugging the drive.  It also shows how to receive alerts from mdadm via e-mail.  I would recommend setting up the e-mail option if at all possible as you may not check /var/log/messages until it's too late (from personal experience).

---

### Post by the real omni on 2009-12-18
> **Nullexe said:**
> The link I posted should be able to show you how to fail the drive manually without physically unplugging the drive.  It also shows how to receive alerts from mdadm via e-mail.  I would recommend setting up the e-mail option if at all possible as you may not check /var/log/messages until it's too late (from personal experience).

Perfect, many thanks!

---

