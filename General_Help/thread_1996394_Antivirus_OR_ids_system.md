---
title: "Antivirus OR ids system"
date: 2012-06-04
forum: General Help
---

### Post by Mgiacchetti on 2012-06-04
I understand that it is the common mindset that linux doesn't need an antivirus solution, as it's linux therefore it's 'safer' than windows. 

However, I don't like the current mindset and would like to find/install a solution that actually scans for linux intrustions.  

I have already installed chkrootkit, and would like to know if there are any other solutions out there that specifically protect linux workstations.

I've looked into installing snort and acid, but don't really want to go through the daunting experience of setting up all the rulesets.

Does anyone know of any solutions that may interest me?

---

### Post by zombifier25 on 2012-06-04
Dunno, but the stickies in [Security Discussions subforum](http://ubuntuforums.org/forumdisplay.php?f=338) may be of interest.

---

### Post by haqking on 2012-06-04
> **Mgiacchetti said:**
> I understand that it is the common mindset that linux doesn't need an antivirus solution, as it's linux therefore it's 'safer' than windows. 

However, I don't like the current mindset and would like to find/install a solution that actually scans for linux intrustions.  

I have already installed chkrootkit, and would like to know if there are any other solutions out there that specifically protect linux workstations.

I've looked into installing snort and acid, but don't really want to go through the daunting experience of setting up all the rulesets.

Does anyone know of any solutions that may interest me?

Well Viruses and intrusions are different things.

The mindset about not needing AV is open to conjecture.

The fact is there are no viruses in the wild which effect Linux, though there could be, the thing is if there was then AV would not detect them anyways so a vicious circle.

AV on linux is for scanning for infections that could spread to windows through shared files.

there is no AV solutions which scans for intrusions.

Viruses are rarely if ever associated with system compromise as most of the payloads are nuisance based.

Malware in general however such as trojans are a different matter.

For intrusions i personally like snort but the process in general is better in a layered approach with firewall policies and rules, log monitoring etc.

There is no one solution which does not require effort and work on your part to achieve the goals you seek.

**Security is a process not a product.**

Read the basic security wiki for a good start and then read the links from there

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity).

Peace

---

### Post by Mgiacchetti on 2012-06-04
> **zombifier25 said:**
> Dunno, but the stickies in [Security Discussions subforum]("http://ubuntuforums.org/forumdisplay.php?f=338") may be of interest.
Yea, I should have checked there first, thx though..


> **haqking said:**
> Well Viruses and intrusions are different things.

The mindset about not needing AV is open to conjecture.

The fact is there are no viruses in the wild which effect Linux, though there could be, the thing is if there was then AV would not detect them anyways so a vicious circle.

AV on linux is for scanning for infections that could spread to windows through shared files.

there is no AV solutions which scans for intrusions.

Viruses are rarely if ever associated with system compromise as most of the payloads are nuisance based.

Malware in general however such as trojans are a different matter.

For intrusions i personally like snort but the process in general is better in a layered approach with firewall policies and rules, log monitoring etc.

There is no one solution which does not require effort and work on your part to achieve the goals you seek.

**Security is a process not a product.**

Read the basic security wiki for a good start and then read the links from there

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity).

Peace
Thanks man Primo advice.

---

### Post by 3Miro on 2012-06-04
There is no program that scans for Linux viruses. If a Linux virus is created, then the proper way to handle the problem is to patch the system and end the threat once and for all. The Windows mindset of relying on 3d party temporary solutions is utter nonsense.

The ability to block processes and look for "suspicious behavior" is handled by SELinux or AppArmor. Ubuntu uses AppArmor by default. If you want to play around with security, look into those two.

---

### Post by Lyfang on 2012-06-04
I don't have (need?) antivirus on Linux systems, check out these links/websites:

5 Known Linux Anti-virus Software for Paranoid Users [http://www.junauza.com/2008/12/5-known-linux-anti-virus-software-for.html](http://www.junauza.com/2008/12/5-known-linux-anti-virus-software-for.html)
Antivirus software for Linux [http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

---

### Post by 3Miro on 2012-06-04
> **Lyfang said:**
> I don't have (need?) antivirus on Linux systems, check out these links/websites:

5 Known Linux Anti-virus Software for Paranoid Users [http://www.junauza.com/2008/12/5-known-linux-anti-virus-software-for.html](http://www.junauza.com/2008/12/5-known-linux-anti-virus-software-for.html)
Antivirus software for Linux [http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

Those link to Linux software that looks for Windows viruses. This is useful if you have a Linux machine that interfaces with Windows ones. However, those programs will NOT improve the security of your Linux machine.

OP talks about AV software that looks for Linux viruses, and there is no such software.

---

