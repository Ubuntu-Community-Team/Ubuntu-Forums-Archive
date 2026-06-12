---
title: "locking printer config"
date: 2010-07-24
forum: General Help
---

### Post by cmcanulty on 2010-07-24
I run 6 machines at our local library with Ubuntu Lucid. Here is a problem. We use a network printer accessed through the ethernet cabling system. It isn't attached to a computer. I want to set it up so the Ubuntu computers find it by ip address, it has a static address. Then I would like to lock down the printer config as each week other printers show up there, all basically the same printer but only works if the patrons pick the correct iteration of it and it doesn't always stick to the default option I haver set up. So people get confused and then pick another one and no prints. I want them to click print and bingo only one printer shows up and it is the ip address I have set up. Ubuntu seems to love to add numerous copies of printers and in this situation it is creating havoc. So can I somehow set a command to lock the printer config and eliminate all this confusion? I hope this is clear as it is a fairly complicated issue.But is reflecting poorly on Linux to people who come in and I want it to b e very stable.I am not very advanced so please answer in simple terms, thank you.

---

### Post by robsoles on 2010-07-24
Please try opening 'System'->'Administration'->'Printing' and deselect "Discovered Printers" under the "View" menu.

Then delete any 'discovered' printers that remain on display (if any) and try that for a bit - if that doesn't do the trick for you then I think we need to know lots more about your printer you have there (I have three printers on the network at work and the 10.04 LTS machines don't "rediscover" them at all).

---

### Post by cmcanulty on 2010-07-25
Yes that works but every time computers reboot discovered printers reappears. It is an HP network printer P2035n

---

### Post by robsoles on 2010-07-25
I see that the option I got you to try for me is purely a matter of 'view' and no more...

Could I get you to do two things for me:

Attack one of the 6 PCs and delete all references to all printers in the printer dialog and restart it, see if you can print on the discovered printer and then, if you can print, restart again and see if it discovers another edition of the printer or what happens - if not then after two hours and a couple more restarts?

When/If that idea falls flat on it's face try this one;

Jump on the WebUI (the control interface available in a browser - tell me if you don't know how to open it) for the printer and go through it's configuration items for 'upnp', 'advertise', 'snmp', 'discoverable' and other items that sound like they may mean it will be advertising itself on the LAN. Once this is done re-delete the nonsense references to the printer on the 6 PCs, keeping the 'real' one, and cross your fingers.


Please let me know if either of these cracks it for you.

---

### Post by cmcanulty on 2010-07-25
Part of the problem is I can't delete the extra printers as usually that option is greyed out. Is there a command or a config file where I could delete them and then lock down the config file? I work at the library and do all their tech stuff on Thursdays so will have to wait to try what you suggested. Thank you and I will get back to this Thursday. This is such an irritant to patrons that they get a negative impression of Linux, though we have no other problems with it and I really enjoy not having to run all sorts of security on them. Also we have a tiny budget and Ubuntu is free. Thanks again and expect another update Thurs of Fri.

---

### Post by robsoles on 2010-07-25
Please attach the file from /etc/cups/printers.conf from one of the 6 PCs to a post on this thread.

Examine the file for yourself and if you see how it works (xml basically) then you can have a bash at modifying it for yourself - if you don't see how it works I am going to have a bash at it for you.

---

### Post by cmcanulty on 2010-07-26
OK thanks very much I will get back on this Thurs when I work on the library computers. I see it says not to edit while cups is running so what is the command to stop and restart cups?

---

### Post by robsoles on 2010-07-26
```
service cups stop
```

to which the opposite is of course

```
service cups start
```

Possibility is that you make the changes and it changes back but we may be able to force it out of changing back once you have a copy you like.

---

### Post by cmcanulty on 2010-07-29
OK I am at library and tried to get the printer set up by ip address but I get a cups error with that. I tried the format [http://192.168.2.112/HP](http://192.168.2.112/HP) LaserJet P2035n. Also here is a copy of the cups file. The problem isn't that I can't install the printer, that is easy. But no matter how many times I uncheck show discovered printers it goes right back to showing them.And even though I set a default printer when patrons hit print it comes up with a big list of 2 to 8 printers that are all basically the same but only one will actually be correct and print. And it isn't always highlighting the default printer.it is OK on Thursdays when I am here but other days people get mad because the printer isn't working. This is a major hassle with Linux.Here is a copy of cups.conf

```
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
Order allow,deny
Allow 192.168.2.*
</Location>
  Encryption Required
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
Order allow,deny
Allow from @LOCAL
Allow 192.168.2.*
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order allow,deny
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order allow,deny
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order allow,deny
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order allow,deny
  </Limit>
  <Limit All>
    Order allow,deny
  </Limit>
</Policy>
LogLevel debug
LogDebugHistory 999999
Port 631
Listen /var/run/cups/cups.sock
```

I have also attached a screenshot of a print dialog, but this is after I just deleted a bunch of printers. Oh and I am attaching another screenhot as alreay another printer has reappeared.We just need something very easy and stable as people come here and want to print but many are very beginning computer users and all they understand is hit print and either it works or not. I did go into the cups website and unchecked show printers shared by other systems but as soon as I did that the 3rd printer appeared. I am really befuddled by this. You suggest deleting all the printers but that doesn't work as delete printer is usually greyed out. I am in the admin account of course.I f you have time and the inclination please call me here at the library until 7pm EDT today at 231-882-4037 or I can call you, we have free long distance here.Also I am printing here the printers.conf file in case that is helpful

```
# Printer configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<DefaultPrinter Hewlett-Packard-HP-LaserJet-P2035n>
Info Hewlett-Packard HP LaserJet P2035n
Location HP
MakeModel HP LaserJet p2035n hpijs pcl3, 3.10.2, requires proprietary plugin
DeviceURI hp:/net/HP_LaserJet_P2035n?zc=NPI898F61
State Idle
StateTime 1280432064
Type 8425500
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 100 foomatic-rip
Filter application/vnd.cups-pdf 0 foomatic-rip
Filter application/vnd.cups-command 0 commandtops
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer HP-910>
Info HP 910
Location HP LaserJet P2035n
DeviceURI file:///dev/null
State Stopped
StateMessage 
StateTime 1280431325
Type 4
Accepting No
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```

---

### Post by robsoles on 2010-07-29
I just got up a couple of minutes ago and have to leave for work in 3 minutes as I type.

As a simpler thing to do for an interim perhaps you can rename the printer "HEY, USE THIS PRINTER" using the Printing dialog from Administration under System.

I am trying to get a machine near me to show me your problem so I can see what I have to do to make it go away but so far I don't have a printer that will do that to Lucid for me.

---

### Post by robsoles on 2010-07-29
Hey, I see differences between your cupsd.conf file and a 'vanilla' one that may be the causes of the problem - basically bits about browsing.

Here is a 'vanilla' one, please consider making a backup of your existing one on one of these machines to replace the contents with this:
```
#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

```
Best case scenario: Just fixes the problem, worst case scenario: you need to put the backup copy of existing one back in place.

In case you can't delete that 'hp910' from the machine you got that 'printers.conf' file from the following should be good replacement guts for the file off that machine but do make a backup of the existing file and remember to stop cups before saving over the existing printers.conf file
```
# Printer configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<DefaultPrinter Hewlett-Packard-HP-LaserJet-P2035n>
Info Hewlett-Packard HP LaserJet P2035n
Location HP
MakeModel HP LaserJet p2035n hpijs pcl3, 3.10.2, requires proprietary plugin
DeviceURI hp:/net/HP_LaserJet_P2035n?zc=NPI898F61
State Idle
StateTime 1280432064
Type 8425500
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 100 foomatic-rip
Filter application/vnd.cups-pdf 0 foomatic-rip
Filter application/vnd.cups-command 0 commandtops
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```

I could be wrong! I suggest following two steps to make backups before proceeding with edits:
```
sudo cp /etc/cups/cupsd.conf /etc/cups/cupsd.conf-20100729-0850
sudo cp /etc/cups/printers.conf /etc/cups/printers.conf-20100729-0850
```

---

