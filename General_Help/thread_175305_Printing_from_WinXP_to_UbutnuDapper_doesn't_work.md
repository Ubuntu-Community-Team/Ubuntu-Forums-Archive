---
title: "Printing from WinXP to UbutnuDapper doesn't work:"
date: 2006-05-13
forum: General Help
---

### Post by Skeletonix on 2006-05-13
Hello!

I have problem with sharing my Ubutnu_printer:confused: . Here is my cupsd conf :

```

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
  Listen 192.168.0.1:631	
# Listen localhost:631
  Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
  Allow 192.168.0.2	
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost

</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
  Allow 192.168.0.2
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
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

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf




```

When I try print on winXP Pc i find in cups accces.log this:

```

192.168.0.2 - - [13/May/2006:12:31:21 +0200] "POST /printers/Stylus-C64 HTTP/1.1" 200 175 Get-Jobs successful-ok
192.168.0.2 - - [13/May/2006:12:31:26 +0200] "POST /printers/Stylus-C64 HTTP/1.1" 200 569 Print-Job client-error-document-format-not-supported

```  

The printer is connect ro winXP machine by htttp://192.168.0.1:631/printers/Stylus-C64. If I try ipp://192.168.0.1:631/printers/Stylus-C64 windows are not able to detect printer!

Where is problem? Why it doesn't work? 
****

---

### Post by cyracks on 2006-05-13
Like this:

[https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/43145]("https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/43145")

---

### Post by Skeletonix on 2006-05-13
..ouch...yeah it's look same..,but what now, wait? :-k

---

### Post by cyracks on 2006-05-14
You can subscribe to the thread so you will be notified for changes and wait or try to help fixing the problem.

---

