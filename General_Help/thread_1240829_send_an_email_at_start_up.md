---
title: "send an email at start up"
date: 2009-08-15
forum: General Help
---

### Post by peterhocking on 2009-08-15
Hi

I have a PC running Ubuntu 9.04 (64 bit) which runs 24/7. The bios in it is set to automatically restart the PC when the power is restored after power failure.

Is it possible to set it up so that it send me an email to say its restarted?

The reason for this is that I want to login to it remotely to check that some processes are running properly.

TIA

Peter

---

### Post by arch0njw on 2009-08-17
Here are a couple of suggestions from the SUSE forums that might work:

1. [http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-04/0501.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-04/0501.html)

2. [http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-04/0536.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-04/0536.html)

The crontab one would be very easy to test, but I would have more confidence that then init script would work.  The syntax the author used for the crontab entry doesn't seem right to me.

---

### Post by Bachstelze on 2009-08-17
> **arch0njw said:**
> The syntax the author used for the crontab entry doesn't seem right to me.

It is perfectly right.

---

### Post by peterhocking on 2009-08-18
> **arch0njw said:**
> Here are a couple of suggestions from the SUSE forums that might work:

1. [http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-04/0501.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-04/0501.html)

2. [http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-04/0536.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2005-04/0536.html)

The crontab one would be very easy to test, but I would have more confidence that then init script would work.  The syntax the author used for the crontab entry doesn't seem right to me.

Thanks for that

Peter

---

### Post by dcstar on 2009-08-19
> **peterhocking said:**
> Hi

I have a PC running Ubuntu 9.04 (64 bit) which runs 24/7. The bios in it is set to automatically restart the PC when the power is restored after power failure.

Is it possible to set it up so that it send me an email to say its restarted?


A simple command string in /etc/rc.local would probably do that, or just use the logcheck package to do something similar.

---

