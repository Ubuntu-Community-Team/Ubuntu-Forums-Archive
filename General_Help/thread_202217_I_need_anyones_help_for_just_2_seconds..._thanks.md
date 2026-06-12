---
title: "I need anyones help for just 2 seconds... thanks"
date: 2006-06-23
forum: General Help
---

### Post by konacoffeeguy on 2006-06-23
Hey, 
  I need somone that has not edited this file

 /etc/cups/cupsd.conf


 from a Dapper release to go to that file and copy and paste their configure file. Mine is messed up and I need a fresh copy. ( I networked two computers together with one printer, but now they are each only using one. ) Anyway, if anyone could help me out by pasting their conf file that would be great, thanks, 

 Konacoffeeguy

---

### Post by tribaal on 2006-06-23
There you go.

Just a tip: try to be more precise when you choose a thread header, something like "Messed up cupsd.conf, can anyone paste his?" would have been much better IMO.
Help people helping you :)

- trib'

---

### Post by Stormbringer on 2006-06-23
Here's a carbon copy of the file ...

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
# Listen localhost:631
# Listen /var/run/cups/cups.sock

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

#
#

```

---

### Post by konacoffeeguy on 2006-06-23
Many thanks to you and your leader (ha ha jk ) Thanks the info helped a lot ,

 Konacoffeeguy

---

### Post by yota on 2006-06-23
Just a tip:

if you broke some files on your system you can repair them by reinstalling the package that contains them. To guess which package contain a specific file you can use
```

dpkg -S <filename>

```
In your specific case something like this (eventually deleting the broken file to ensure a clean reinstall) should have worked:
```

yota@linbook:~$ sudo dpkg -S cupsd.conf
Password:
cupsys: /usr/share/man/man5/cupsd.conf.5.gz
cupsys: /usr/share/cups/doc-root/help/man-cupsd.conf.html
cupsys: /etc/cups/cupsd.conf
kdelibs-data: /usr/share/apps/kdeprint/cupsd.conf.template
yota@linbook:~$ sudo apt-get install --reinstall cupsys

```

---

