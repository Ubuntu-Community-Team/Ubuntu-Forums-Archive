---
title: "ClamAV Sleep Issue"
date: 2010-01-28
forum: General Help
---

### Post by philrm on 2010-01-28
Hi
 
I'm having a bit of a prob using ClamAV on my Ubuntu system. If I leave the PC while ClamAV is scanning a volume, it will pause, or kind of go to sleep while I am away. When I return and move the mouse, it continues scanning. The screen does not blank, it's just the ClamAV scan that seems to pause.
 
I have checked my system settings and confirmed that all power setting within ubuntu are disabled, so the system itself shouldn't go to sleep or hibernate... therefore I am assuming that this is an issue with ClamAV itself - particularly as I haven't experienced anything similar with any other package.
 
Has anyone else experienced anything similar and if so do you know of a way around it?
 
Thanks!
 
philrm

---

### Post by phillw on 2010-01-28
Hi and welcome to the Forums

ClamAV searches for win viruses, you only need it to scan a WINE installation or files you've downloaded before copying / moving them to a Win environment. ClamAV is typically used on mail servers to scan attachments for said nasties. Those nasties won't work on ubuntu - they're written solely for Win systems. > Clam AntiVirus is a GPL anti-virus toolkit for UNIX. The main purpose of  this software is integration with mail servers (attachment scanning).

There's some additional information on ClamAV here --> [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

I have ClamAV daemon running as I have an email server on my system for testing with. I actually use Bitdefender for scanning files for transfer - Odd, yes, but I was using Bitdefender before I was using Clam - lol

Regards,

Phill.

---

### Post by philrm on 2010-01-28
Hi 
 
Thanks for your reply :)
 
I understand that ClamAV is used to scan for windows viruses - I mainly use this software to scan USB drives that are used on windows machines to check that they are safe.
 
The problem I have is that when I attempt to scan a USB drive using ClamAV I have to sit there the whole time, moving the mouse about - if I don't then the scan pauses as if the software has gone to sleep!
 
It seems like a strange issue, I've tried reinstalling the software but to no avail, and tbh I'm stumped..!
 
philrm

---

### Post by phillw on 2010-01-28
A cheat, I know - But, try Bitdefender ..

[http://www.vpolink.com/threads/495-Anti-Virus-for-Linux](http://www.vpolink.com/threads/495-Anti-Virus-for-Linux)

Once you've downloaded it, it will appear in Applications --> System Tools.

soz I can't help with the ClamAV issue, as I don't use it for scanning files - it's there for my mail server to use and abuse.

Regards,

Phill.

---

### Post by philrm on 2010-01-28
Thanks, Bitdefender looks good so I'll certainly give that a go.
 
Contrary to what I said in my first post, I'm wondering now if it might be the OS rather than ClamAv - I've just noticed it with something else. I was installing a package, all seemed to be going fine so I left the PC, came back 10 minutes later and everything had stopped. I moved the mouse and it continued the installation.
 
Is there anything other than power management settings that could cause something like this to happen?
 
philrm

---

### Post by phillw on 2010-01-28
> **philrm said:**
> Thanks, Bitdefender looks good so I'll certainly give that a go.
 
Contrary to what I said in my first post, I'm wondering now if it might be the OS rather than ClamAv - I've just noticed it with something else. I was installing a package, all seemed to be going fine so I left the PC, came back 10 minutes later and everything had stopped. I moved the mouse and it continued the installation.
 
Is there anything other than power management settings that could cause something like this to happen?
 
philrm

The only other setting that would cause it is your Screen-Saver - try turning the time upto something like 1 hour.

Phill.

---

### Post by philrm on 2010-01-28
I just checked on the screen saver and it was already disabled :( 
 
I'm going to download 9.10 for a fresh install (been meaning to for a while now) so hopefully this will solve it. 
 
Thanks for your advice!
 
philrm

---

### Post by Seq on 2010-01-28
> **philrm said:**
> Contrary to what I said in my first post, I'm wondering now if it might be the OS rather than ClamAv - I've just noticed it with something else. I was installing a package, all seemed to be going fine so I left the PC, came back 10 minutes later and everything had stopped. I moved the mouse and it continued the installation.
 
Is there anything other than power management settings that could cause something like this to happen?

In the past there has been weird problems where the machine would seemingly hang until input was received (Although I think typically any sort of interrupt would work -- input is easy). Unfortunately I can't find anything other than issues against 2.6.27, nothing current from a quick glance.

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/273318](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/273318)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254668](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254668)

If this is easily reproducible, I'd suggest trying with acpi=off and reproducing.

Regardless, you should file a bug as this is not expected behaviour.

---

### Post by philrm on 2010-01-29
Thanks to both of you for your advice. I downloaded and installed 9.10 and this has resolved the issue :)

---

