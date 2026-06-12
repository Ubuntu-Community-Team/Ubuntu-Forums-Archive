---
title: "[X]ubuntu does not print to SHARP"
date: 2010-05-22
forum: General Help
---

### Post by isaacd on 2010-05-22
Hello.

_**The Problem:**_ the computer does not print to the SHARP Copier: Idle - /usr/lib/cups/backend/dnssd failed.

_**The System:**_
Xubuntu 10.04
SHARP MX 6200N (using the "Sharp MX-4501N Foomatic/pxlcolor" driver, because there is no SHARP MX 6200N driver)
The computer name is: Gregory
The printer/copier name is: PETER
PETER is on a windows network.

_**The context:**_
I set up the computer to work use this printer. When I tried Windows printer via SAMBA, it told me that there were no printer shares, but on the printer dialog sidebar, right under the network printer header, it gave me a couple choices, one of which was SHARP MX 6200N, which I chose and set up. It printed the test page just fine. Now I am back a week later and I print a test page and it does not work:  Idle - /usr/lib/cups/backend/dnssd failed.

I susspect that something about the network has changed since then (a computer turned off, etc.) However, the server is on as while it is failing to print.

[U][B]Things I have already tried:
[/B][/U][INDENT]musicdirector@Gregory:~$ sudo service avahi-daemon restart
avahi-daemon start/running, process 2079
musicdirector@Gregory:~$ sudo service cups restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
[/INDENT]Help would be apreciated.
Thanks.
     Isaac.

---

### Post by isaacd on 2010-05-23
Self Solved:

Firestarter was not nixing any connection I tried to make to the printer. I had to add some rules and then it worked.

---

### Post by pmwangi80ke on 2011-12-17
> **isaacd said:**
> Self Solved:

Firestarter was not nixing any connection I tried to make to the printer. I had to add some rules and then it worked.



Hello,

I have a sharp AR-5316E am trying to install in ubuntu 10.10 but i cant get drivers for it. It is listed as paperweight in the open printing database(i dunno what that means) Please help me out....

peter

---

