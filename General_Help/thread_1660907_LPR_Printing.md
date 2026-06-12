---
title: "LPR Printing"
date: 2011-01-06
forum: General Help
---

### Post by davo963320 on 2011-01-06
I'm at my wit's end!

Panasonic Workio DP-1520 on ip: 192.168.10.100

Printing a test page seems to work fine as far as cups is concerned - acts as though it has successfully processed/transfered the print job etc except the printer is braindead - doesn't even flinch, no spooling/whirring NOTHING. no errors - just no printing either!!

nmap shows port 515 open, service: printer

in cups the printer is recognised when adding a printer (ie comes up during network scan)

I've tried just about every single generic .ppd (PCL 6, 5e etc) as well as the .ppd provided by panasonic for mac/windows

The url i'm using is:

lpd://192.168.10.100/Pana1520 (i've tried "LPT0, LPT1, lp, plus just about every other combination that shows up when the printer is 'probed' etc)

The closest thing I've had to the printer doing anything under ubuntu is by telnet via port 515 and typing ^D to which i get the response "It is not being supported." haha.

Under xp - printer works fine by adding as a local printer printing to a Standard TCP/IP Port with LPR selected and the queue is "Pana1520".

This is an ongoing problem as it is an expensive photocopier in our office and I'm trying to migrate our workstations to ubuntu - I've been trying since 9.10 with no success =(.

I've seen references to printers being proprietary GDI/windows etc but surely there has got to be the way because there is no way I'll be able to convince the boss to sink $5k in a replacement photocopier and i'm trying to avoid running XP in a vm on the server just to get the printer going... =(

---

