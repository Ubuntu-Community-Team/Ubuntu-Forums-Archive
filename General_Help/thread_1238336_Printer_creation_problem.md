---
title: "Printer creation problem"
date: 2009-08-12
forum: General Help
---

### Post by gerryarmstrong on 2009-08-12
Guys,
I have a problem trying to install a printer in my newly installed Ubuntu Jaunty setup. When I try to open System->Administration->Printing I get the box flash on th screen for about a second then disappear. I can open the System->Preferences->Default but this does not help as I can not add any printers.
I followed some online suggestion to do the following:
sudo apt-get --reinstall install cupsys*
sudo /etc/init.d/cups restart

Still no joy. Any suggestions?
cupsd.conf below:
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
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
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
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
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
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

---

### Post by gerryarmstrong on 2009-08-13
Guess no one can assist me with this one... looks like a re-install again!

---

### Post by Brian R. on 2009-08-14
I hope you get an answer as i have some thing of the same problem, but with me the Printer Configuration-localhost dialog window comes up but the configuration program siezes. With me i do not know if it is a ubuntu 9.04 problem, or the fact that i was using the printer when it was plugged into a vista machine and shared. The windows machine is not plugged in at the moment and the printer has been transfered to the ubuntu machine, which installed the software without prompting, but i cannot get into the configuration program.
Brian R.

---

### Post by Brian R. on 2009-08-17
Try sudo apt-get install --reinstall system-config-gnome

---

