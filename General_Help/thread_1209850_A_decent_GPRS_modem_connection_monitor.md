---
title: "A decent GPRS modem connection monitor?"
date: 2009-07-10
forum: General Help
---

### Post by bwucke on 2009-07-10
I just got a new GPRS modem for my netbook (eeebuntu) and it worked almost without a hitch. It works fine now, except NetworkManager is very terse about it. Since I'm paying for network traffic (each 100KB sent/received), I'd like to be able to monitor my network usage = expenses, to avoid network-heavy software, pages that keep downloading more data and so on. So I need a program that would just display "bytes sent" and "bytes received" along with some useful information.

Something that would do what I need is UMTSmon, except it has all the "set up the connection" stuff which I don't need (just a monitor for existing connection, not a dialer), and it's not supported by Ubuntu (considered "obsolete because now Network Manager does all of this" except it does not, it handles only the dialer part, not the display stats part). so I'd prefer something more Ubuntu-compliant. 

[IMG]http://to2k.com/wp-content/uploads/2008/06/UMTSmon.png[/IMG]

Maybe a normal modem monitor can do this as well (sans network power of course) - in this case could you recommend one?

---

### Post by solitaire on 2009-07-10
you could install "vnstat" (it's in the repos)
> 
vnStat is a network traffic monitor for Linux. It keeps a log of
daily network traffic for the selected interface(s). vnStat is not
a packet sniffer. The traffic information is analyzed from the /proc
filesystem, so vnStat can be used without root permissions.


Think their is a web front end for reporting the usage but not sure.

---

### Post by bwucke on 2009-07-13
Thanks, but since it's a netbook, I'd prefer to avoid installing a web server on it.
Any chance for something more desktop-friendly? Panel applet or something like that?

---

### Post by juanJosepablos on 2009-10-13
Maybe:
Network Traffic Monitor
[http://sourceforge.net/projects/netramon/](http://sourceforge.net/projects/netramon/)

I have not test it yet, but it looks promising.

---

