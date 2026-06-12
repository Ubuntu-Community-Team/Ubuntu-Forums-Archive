---
title: "Connecting to CUPS Server"
date: 2010-07-25
forum: General Help
---

### Post by lewisforlife on 2010-07-25
I have a CUPS server on Debian, I am trying to connect from an Ubuntu 8.04 box.  Here is my CUPS configuration file on Debian just in case it is usefull:

```

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
DefaultAuthType Basic
DefaultEncryption IfRequested
<Location />
  Allow localhost
  Allow 192.168.1.*
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Allow localhost
  Allow 192.168.1.102
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

When I try to add a printer I have set up in CUPS from my Ubuntu box, it asks for the password for katie (this is the user that is logged in on ubuntu box) on 192.168.1.200 (CUPS Debian Box).  The problem is, I don't have a katie user set up on the debian box, am I supposed to for this to work.  Why is it even prompting for a password?  Also, it won't let me change the name so that I can authenticate with a different user, it is not in a text box.

---

### Post by Morbius1 on 2010-07-25
Are you attempting to access the debian printer using CUPS and the "Windows printer via Samba" option?

Or are you using :

ipp://192.168.1.200:631/printers/Debian-Printer-Name

---

### Post by lewisforlife on 2010-07-25
> **Morbius1 said:**
> Are you attempting to access the debian printer using CUPS and the "Windows printer via Samba" option?

Or are you using :

ipp://192.168.1.200:631/printers/Debian-Printer-Name

There is no Windows printer involved here.  But I am trying to install the Debian printer that is configured in CUPS on my Ubuntu box.  I am just going to System->Administration->Printers.  The printer is showing there, but when I click on add printer I am not able to, see my above post.

---

### Post by AlphaLexman on 2010-07-25
My first impression is that this a network issue, not a cups or printer issue.
Is your router blocking port :631?
Can you point a browser to:
```
http://localhost:631
```

---

### Post by lewisforlife on 2010-07-25
I was a little confused.  I was attempting to add a new printer on the Debian box from the Ubuntu box, I was actually wanting to add a printer to the Ubuntu box, which already seemed to have been by default.  This is why I was getting the authentication box, because Katie was not on the Debian box.  I have it figured out now.  Thanks for the help.

---

