---
title: "WinSCP: this is end-of-file:0 via Putty?"
date: 2009-07-19
forum: General Help
---

### Post by markytheone on 2009-07-19
Hi guys, I installed scp-only via apt last night and all was fine. When I went to SSH into my server this morning all I get is WinSCP: this is end-of-file:0 no matter whats command I issue.

Heres what it looks like:

WinSCP: this is end-of-file:0
sudo bash
WinSCP: this is end-of-file:0
reboot
WinSCP: this is end-of-file:0


Thanks for your help.

---

### Post by markytheone on 2009-07-19
Guys I dont know how to put this but this at the moment this production box is dead in the water. I cannot SSH into the box and I am out of resources from Google.

Marky

---

### Post by blueridgedog on 2009-07-19
I am a bit confused.  You installed WinSCP on the workstation you are ssh'ing from or on the server?  Each run Linux/Ubuntu?  You get the error when you attempt to ssh or after getting an ssh connection?

---

### Post by markytheone on 2009-07-20
I installed the package scp-only onto my Ubuntu server. Using Putty from my Windows vista Laptop, once I have logged in I get:

login as: markytheone
[EMAIL="stuart@voice.bluewave.im"]stuart@voice.bluewave.im[/EMAIL]'s password:
Linux voice 2.6.24-19-server #1 SMP Wed Jun 18 15:18:00 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Sun Jul 19 10:46:46 2009 from ***

WinSCP: this is end-of-file:0


Please help!!

---

### Post by blueridgedog on 2009-07-20
I found this on a mailing list archive:

[http://lists.ccs.neu.edu/pipermail/scponly/2004-December/000673.html](http://lists.ccs.neu.edu/pipermail/scponly/2004-December/000673.html)

It links the error to a shell directive.

Do you have physical access to the server?

Have you tried other ssh clients?

---

