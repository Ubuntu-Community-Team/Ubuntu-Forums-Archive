---
title: "Network printer doesn't work after upgrading to 10.04"
date: 2010-11-08
forum: General Help
---

### Post by Hostage_ on 2010-11-08
Hi,
I have recently upgraded to 10.04 and subsequently to 10.10.
I have a network printer Lexmark C530dn. Before the upgrade to 10.04 it work OK.
After the upgrade  i have this problem: When i print something it goes right to completed jobs, without an error and without printing.
My user is allowed to print, I checked that.\
this is from the access log:
localhost - - [08/Nov/2010:20:38:58 +0100] "POST / HTTP/1.1" 200 253 Create-Printer-Subscription successful-ok
localhost - - [08/Nov/2010:20:39:10 +0100] "POST /printers/Lexmark-C530 HTTP/1.1" 200 205765 Print-Job successful-ok
When i print the self-test page, it prints fine, so I assume the problem's in the system rather than the printer.
Thanks for any help.

---

### Post by efflandt on 2010-11-08
Maybe cups is having trouble finding your printer by DNS or netbios name.  I had that problem recently, maybe because I am doing double NAT (wireless died on wireless/modem/router) and the printer is on the WAN side of my wireless router.

Although, if that happens you usually get a printer icon in upper right panel that something is waiting in the queue (but no errors in logs).

If you right click on that printer and go to Properties, see what the URI shows.  I forget what mine was because I changed all my computers already, but I simply changed it to **socket://ip_address:9100** and that worked (port 9100 is a JetDirect thing, but the Lexmark print server understands that).  A short time after I did that, the jobs in the queue printed.

I just test printed from a laptop that I had upgraded in the past month from 9.10 to 10.04 and it works fine (as do 64-bit 10.04 installed from scratch and 10.10).

I have a Lexmark C543dn which worked with C534dn driver before I found the C540 series ppd's (now in current Ubuntu versions).  If all else fails, try removing and reinstalling the printer.

---

### Post by Hostage_ on 2010-11-09
i tried deleting and re-adding and it didn't work.
I changed the URI as well, and there was no change.
Any ideas anyone?

---

### Post by Hippytaff on 2010-11-09
This might be worth a read :-)
 
[http://www.cups.org/articles.php?L198+TFAQ+Q](http://www.cups.org/articles.php?L198+TFAQ+Q)

---

