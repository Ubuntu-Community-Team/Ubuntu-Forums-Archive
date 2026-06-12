---
title: "Samba-printer-problem"
date: 2006-04-09
forum: General Help
---

### Post by Johanc on 2006-04-09
Hey

For to days I have know tried to get networkprinting. But I haven't succeded. I have shared a printer on a desktop-computer running Ubuntu (of course :p ). And I have given the printer these options in /etc/samba/smb.conf: 

...
[I][printers]
comment = All printers
path = /var/spool/samba
browseable = yes
public = yes
writable = yes
printable = yes
guest ok = yes[/I]


The gnome-printer-configuration-thing finds a network printer, but gives med this message:

*Ready: Unable to get printer status (client-error-forbidden)!*

My /etc/cups/cupsd.conf looks like this: 

[I]DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.1
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location> 
[/I]

Can anybody help me solve this problem??

---

### Post by drpaul on 2006-04-09
Have you told Samba you're using cups?  My smb.conf has this in it

   load printers = yes
# Additions from Peter's Blog
  browseable = yes
#  printable = yes
  public = yes
  create mode = 0700
  guest only = yes
  use client driver = yes
  path = /tmp

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

Note that the printalbe = yes is commented out in the general settings. I then have a specific printer share as

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

This works for me as I am serving to a Windows XP computer.

HTH

Paul

---

### Post by Johanc on 2006-04-09
Your a champ!!! :) 

This solved my problem.... Thank you very much...

I ow you bro' :D

---

