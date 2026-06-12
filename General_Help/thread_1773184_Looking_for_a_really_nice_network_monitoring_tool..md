---
title: "Looking for a really nice network monitoring tool...your opinion?"
date: 2011-06-01
forum: General Help
---

### Post by 3xp10r3r|X13 on 2011-06-01
hello there everybody,
I've got just one single question for you:

What is the best (not wanting to start a huge discussion) network monitoring tool out there, which is running in a console. 

doesn't have to be some super, multifunctional tool - a great simple and stable thing would be great as well. (multifunctional is awesome as well, so any suggestions are welcome)

--> it should be able to run under slackware, so the best would be probably a tar.bz2 file

Any proposals are appreciated

---

### Post by Joe of loath on 2011-06-01
Monitoring for what, exactly?

---

### Post by bodhi.zazen on 2011-06-01
tcpdump or snort

---

### Post by CVGH on 2011-06-01
iptraf and iftop are handy.....

---

### Post by ruffEdgz on 2011-06-01
> **Joe of loath said:**
> Monitoring for what, exactly?

I have to agree with this comment but some monitoring tools I like would be:
[LIST]
[*]top
[*]conky (desktop only)
[*]sysstat
[*]cacti (web service)
[/LIST]
Just to name a few ;)

---

### Post by Capone on 2011-06-01
netstat if you want to go deep
iptraf if you want less detail

---

### Post by Habitual on 2011-06-01
> **3xp10r3r|X13 said:**
> ...network monitoring tool...which is running in a console.

snmp:
[http://www.net-snmp.org/wiki/index.php/Tutorials#Net-SNMP_Command_Line_Applications](http://www.net-snmp.org/wiki/index.php/Tutorials#Net-SNMP_Command_Line_Applications)

---

### Post by 3xp10r3r|X13 on 2011-06-02
Thanks a lot for all your advices. Finally I ended up with iptraf (is quite nice), but I will try the other ones out as well (for more detailed information, not just the bandwidth I'm currently using).

:D

---

### Post by 3xp10r3r|X13 on 2011-06-02
sry, if this happens to be a really stupid question, but when I try to run ./install-sh, I'm getting the message "install: no input file specified".

--> snort looks great, but I'm already failing to install it

usually I'm just able to run ./Setup or something similar

- new to slackware, so I didn't get used to all the actual linux stuff, yet -

PS: unfortunately there isn't a read me file..
edit: there is a whole directory full with read me files...sry, didn't expect a whole directory (called "doc")

---

### Post by 3xp10r3r|X13 on 2011-06-02
all right, it was a stupid question - you have o run ./configure . Well it just seems as I'm missing the libdnet library....

---

### Post by 3xp10r3r|X13 on 2011-06-02
Everything works perfectly fine. I just had to install libdnet and daq 0.5. Sry. I've bothered you with those little issues.

I like snort :)

---

