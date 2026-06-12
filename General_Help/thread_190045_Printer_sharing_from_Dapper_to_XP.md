---
title: "Printer sharing from Dapper to XP"
date: 2006-06-05
forum: General Help
---

### Post by sasherm13 on 2006-06-05
I am at my wits end here.  I need to share my HP PSC1315 from my Dapper machine to my XP machine.  I have looked all over the web and forums for the proper config for samba and cups and yet it just doesn't seem to work.  Can someone please lay this out for me?

---

### Post by Kilz on 2006-06-05
[QUOTE=sasherm13]I am at my wits end here.  I need to share my HP PSC1315 from my Dapper machine to my XP machine.  I have looked all over the web and forums for the proper config for samba and cups and yet it just doesn't seem to work.  Can someone please lay this out for me?[/QUOTE]

In XP
Start, Control panel, Printers and Faxes, right click , select add a printer.
Add a printer Wizzard starts.
Click on the A network printer or a printer attached to another computer.
Click browse for a printer, then Next. select, then next untill your done.

To be honest I couldnt get XP on my wifes computer to see my printer, so I put it on hers and set it up in sharing by right clicking on the printer. Then used looked for a network printer in ubuntu.

---

### Post by CronoDekar on 2006-06-05
This is slighly outdated, but this is what worked for me:

[https://wiki.ubuntu.com/NetworkPrintingFromWinXP](https://wiki.ubuntu.com/NetworkPrintingFromWinXP)

The main difference is that under <Location /> it should just be "Allow" rather than "Allow from."  Also, I comment out the ports Include at the end and just put Port 631 in the file.  So basically the relevant parts end up like this:

```

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock
Port 631

```

```

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
  Allow 192.168.1.0/24
</Location>

```

(And the # Include /etc/cups/cups.d/ports.conf at the end... though if you want to you could just add Port 631 to that file instead.)

Of course, change that IP to whatever your network uses (the /24 makes it so it includes a whole bunch of 192.168.1.x addresses... I think you can also do /255.255.255.0 for a subnet mask instead).  Be sure any firewalls are allowing the data through and the http listed is typed right.  Oh, and if you haven't gotten it working, you'll probably need to set up your printing computer as having a static local IP through your router.

Wish it was more intuitive, but oh well.

---

### Post by llamakc on 2006-06-05
The above worked for me also.

---

