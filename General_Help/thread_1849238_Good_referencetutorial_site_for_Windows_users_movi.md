---
title: "Good reference/tutorial site for Windows users moving to Linux?"
date: 2011-09-24
forum: General Help
---

### Post by davoutuk on 2011-09-24
Can anybody recommend any tutorials or web sites aimed at helping experienced Windows users migrate to Ubuntu Linux?

I'm a Windows software developer, and understand the basics of what Linux offers.

Initially I'm trying to find help on the purpose of the various folders (e.g. bin, dev, etc, opt etc)

TIA

---

### Post by haqking on 2011-09-24
> **davoutuk said:**
> Can anybody recommend any tutorials or web sites aimed at helping experienced Windows users migrate to Ubuntu Linux?

I'm a Windows software developer, and understand the basics of what Linux offers.

Initially I'm trying to find help on the purpose of the various folders (e.g. bin, dev, etc, opt etc)

TIA

What you refer to is known as the FSH or Filesystem heirarchy.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

As for the rest, i will give my standard answer which i use for similar questions.  The most important aspect to always remember is that Linux is not Windows, was not based on windows and never tries to be windows. Your biggest hurdle is not that Linux is complicated as it may seem to some, but that it is unfamiliar territory for you coming from Windows, also it is very powerful and you have complete control over the system, due to this it can often seem complicated and granted certain things can often be very granular if you like ;-)

Linux can be daunting due to unfamiliar terrritory but to become a confident user only comes only with experience and read, read, read and try, try try then there are at least some basics needed.

First of all i suggest getting to get grips with the security model early on, as there is alot of misunderstanding about Viruses in Linux and malware in general etc so i refer you first to the importance of using sudo here at:

**Security**

rootsudo (**very important you read this one**)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

here for security in general

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and these stickies (in my signature)

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

here for virus information

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

and this will give you a good grounding in the security of your system and such like.

**Virtualisation and testing**

After that it is a case of play, setup virtual machines so you can play without trashing your machine, see:

[www.virtualbox.org](www.virtualbox.org)

and this sub-forum [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

that way you can play with partitions and CLI etc without risking anything.

**Command Line (terminal)** This is where the power lies


[https://help.ubuntu.com/community/Be.../BashScripting](https://help.ubuntu.com/community/Be.../BashScripting)

[http://linuxcommand.org/](http://linuxcommand.org/)

**Apps and Games and Productivity**

Then it comes down to what you want do and achieve, try the following for a starter:

[http://www.makeuseof.com/tag/10-appl...tu-lucid-lynx/](http://www.makeuseof.com/tag/10-appl...tu-lucid-lynx/)
[http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/](http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/)
[http://blog.sudobits.com/2011/03/07/...-ubuntu-games/](http://blog.sudobits.com/2011/03/07/...-ubuntu-games/)

There is so much, it is a case of where do you start.

These are mainly Desktop related, but you may also need or want to look at servers and services so here is a good read:

**Server and Services**

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)


Hope this help, enjoy

Have fun

Regards

haqking

---

### Post by dino99 on 2011-09-24
look at links below

---

