---
title: "Nanny Parental Control timelimit doesn't work"
date: 2010-11-17
forum: General Help
---

### Post by wko on 2010-11-17
I use the Ubuntu 10.10 netbook remix. To limit the time of kids using the netbook I installed Nanny and set the timelimit to 0,5 h.

But for some reason it doesn't work. You can see the Nanny Icon, but it isn't logging of the user when the timelimit is reached...

Did anyone encounter the same problem or is it just me who did something wrong?

---

### Post by trouthunter on 2010-12-12
I'm having the same problem. The user can login, but the notification says "X hours until the session can be used"

It does not work on any computer that I have tried with.

Any one having the same problems?

Ubuntu 10.10 standard desktop

---

### Post by Consecrated on 2010-12-29
Gnome Nanny doesn't work for me on Ubuntu 10.10 64bit. I wish it worked.

I just found this thread, check it out: [http://ubuntuforums.org/showthread.php?t=843510&highlight=parental+controls](http://ubuntuforums.org/showthread.php?t=843510&highlight=parental+controls)
========================================
Copied from above thread.
========================================

List of filtering solutions/projects:
WebContentControl: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)
Webstrict: [http://www.ubuntume.com/webstrict](http://www.ubuntume.com/webstrict) + [https://launchpad.net/webstrict](https://launchpad.net/webstrict)
GChildCare (not yet available): [https://launchpad.net/gchildcare](https://launchpad.net/gchildcare)
UbuntuCE's Parental control GUI: [http://linux.softpedia.com/get/Secur...ol-24501.shtml](http://linux.softpedia.com/get/Secur...ol-24501.shtml)
Squid+Squidgard:
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard) + [http://www.squidguard.org/](http://www.squidguard.org/)
SmoothGuardian (by the creator of DansGuardian, commercial version with web-based easy to use interface): [http://smoothwall.net/products/smoothguardian2008/](http://smoothwall.net/products/smoothguardian2008/) + [http://dansguardian.org/?page=smoothwall](http://dansguardian.org/?page=smoothwall)
MintNanny: [http://www.linuxmint.com/blog/?p=350](http://www.linuxmint.com/blog/?p=350)
MoBlock, an IP blocker: [http://moblock.berlios.de/](http://moblock.berlios.de/)
TimeKpr, track and control account usage: [https://launchpad.net/timekpr](https://launchpad.net/timekpr)
Discussion about K9 web protection GNU/Linux port: [http://forums.bluecoat.com/viewtopic...=a&hilit=linux](http://forums.bluecoat.com/viewtopic...=a&hilit=linux) (suggested by eric.duveau)
Mandriva Linux Parental Control: DrakGuard: [http://www.mandriva.com/enterprise/e...ux-2008-spring](http://www.mandriva.com/enterprise/e...ux-2008-spring) and [http://rpm.pbone.net/index.php3/stat...oarch.rpm.html](http://rpm.pbone.net/index.php3/stat...oarch.rpm.html)
A content filtering solution for Linux-based netbooks (proprietary): [http://www.mobicip.com/online_safety/netbooks](http://www.mobicip.com/online_safety/netbooks)
Gnome Nanny (under development): [http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/) or [https://launchpad.net/nanny](https://launchpad.net/nanny)
Timedoctor, a closed-source cross-platform time-tracking solution, does not block: [http://www.timedoctor.com/index.php](http://www.timedoctor.com/index.php)
Related links: [http://www.rescuetime.com/](http://www.rescuetime.com/) (no GNU/Linux support) and [http://www.timedoctor.com/blog/2010/...an-rescue-time](http://www.timedoctor.com/blog/2010/...an-rescue-time)

DNS filtering:
OpenDNS (suggested by forger): [http://www.opendns.com/](http://www.opendns.com/)
GNU/Linux Desktop parental control based on Opendns.com by Eric Duveau: [http://forums.opendns.com/comments.p...#Comment_18690](http://forums.opendns.com/comments.p...#Comment_18690)
ScrubIT: [http://www.scrubit.com/](http://www.scrubit.com/)

Kiosk specific (for internet cafes, etc):
Kiosk: [http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)
Lock down KDE settings: [http://jriddell.org/programs/kiosk-article.html](http://jriddell.org/programs/kiosk-article.html)
Lock down Gnome settings + disable virtual terminals: [http://www.redhat.com/docs/manuals/e...mand-line.html](http://www.redhat.com/docs/manuals/e...mand-line.html)
Disable ctrl+alt+backspace: [http://www.redhat.com/docs/manuals/e...f-serverf.html](http://www.redhat.com/docs/manuals/e...f-serverf.html)
KDE Kiosk Admin Tool: [http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)
Ubuntu server and DansGuardian for filtering public wireless access: [http://www.branchdistrictlibrary.org...nsguardian.php](http://www.branchdistrictlibrary.org...nsguardian.php)

Firefox specific:
[http://kb.mozillazine.org/Parental_controls](http://kb.mozillazine.org/Parental_controls)

Firewalls and blocking MSN:
NuFW: An authenticating firewall: [http://www.nufw.org/](http://www.nufw.org/)
How to block MSN: [http://blog.eglis.com/index.php/post...e-protocol-MSN](http://blog.eglis.com/index.php/post...e-protocol-MSN) (French)

For Windows:
LogProtect (Windows only, but Free/Libre Software): [http://www.logprotect.fr/](http://www.logprotect.fr/)
K9 Web Protection (proprietary): [http://www1.k9webprotection.com/](http://www1.k9webprotection.com/)
Time control on Windows: [http://www.dougknox.com/xp/tips/xp_restrict_users.htm](http://www.dougknox.com/xp/tips/xp_restrict_users.htm) and [http://www.builderau.com.au/program/...9282967,00.htm](http://www.builderau.com.au/program/...9282967,00.htm)

Useful links:
Setup without iptables: [http://www.vollmar.ch/dansguardian-e.html](http://www.vollmar.ch/dansguardian-e.html)
Sarg - Squid Analysis Report Generator: [http://sarg.sourceforge.net/sarg.php](http://sarg.sourceforge.net/sarg.php)
DansGuardian Documentation Wiki: [http://contentfilter.futuragts.com/w...?id=main_index](http://contentfilter.futuragts.com/w...?id=main_index)

How it works:
Note: Tinyproxy is equivalent to Squid and Firehol is equivalent to iptables (FireHol manages iptables).
[http://dansguardian.org/?page=dgflow](http://dansguardian.org/?page=dgflow) (except that WebContentControl forces the use of the proxy through FireHol)
[http://www.zephyrsoft.net/files/linu...ring-howto.pdf](http://www.zephyrsoft.net/files/linu...ring-howto.pdf) (Picture inside, as well as script for mailing banned sites access attempts to someone)

---

### Post by frontalier on 2011-01-11
> **trouthunter said:**
> I'm having the same problem. The user can login, but the notification says "X hours until the session can be used"

It does not work on any computer that I have tried with.

Any one having the same problems?

Ubuntu 10.10 standard desktop


Same here with 10.10.
:sad:


Anybody knows how to get it running?

---

### Post by wko on 2011-01-11
I just switched to timekpr and it works very good for me.

So if you just want to limit the user login times, timekpr is the better choice until somebody fixes this bug in nanny.

---

### Post by ramjet_1953 on 2011-03-21
I tried Gnome Nanny and like most other people, I found that it just doesn't work.
It shows how much time is left, but when the time is exceeded, it does not end the session. What's more, you can log-on even when the session-time has expired.

Another big problem that I have encountered is a huge memory leak.
see this bug report:
[https://bugs.launchpad.net/ubuntu/+source/nanny/+bug/677879](https://bugs.launchpad.net/ubuntu/+source/nanny/+bug/677879)

I seriously doubt whether this package is being actively maintained.
If you go to the Gnome Nanny site and look at the current list of bugs, there are reports that were submitted over a year ago that still have an unconfirmed status.

I find this disappointing, as this package showed promise in providing an easy way to implement parental control.

Yes, I know that there are things like Dan's Guardian but you need to be a real geek to be able to implement it.

This is one area where Linux trails the user friendly offerings that have been available for Windows for years.

Regards,
Roger

---

### Post by shane2peru on 2011-04-08
I have used timekpr for quite a while, however it is not continuing to be developed, and in light of the Natty release coming soon, I'm looking for alternate solutions.  I gave Nanny a try, but it doesn't limit the time, any ideas for this would greatly be appreciated!

Shane

---

### Post by WarrenL on 2011-07-13
I've just tried Nanny (on Natty), and along with everybody else here, I found it didn't work.

Timekpr is also not working for me. It fails to log the user off when time's up.

Any ideas?

---

### Post by erms on 2013-04-27
I have noticed that the problem is a shift in the hours. For example, when I set to block the internet between 2 and 6 p.m., the program blocked between 10 a.m. and 2 p.m.. Once I've noticed it I bypassed this minor problem.

---

