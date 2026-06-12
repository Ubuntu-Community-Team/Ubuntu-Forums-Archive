---
title: "CUPS Query"
date: 2010-02-24
forum: General Help
---

### Post by marshmallow1304 on 2010-02-24
I just set up a Debian server with SSH and CUPS.  I've set up my cupsd.conf, logged into the web interface and added the printer, but how do I add it in my client which runs Ubuntu?  I've defined my server in /etc/hosts on the client as well.

---

### Post by marshmallow1304 on 2010-02-25
bump


Maybe it'll help if I break this up into three basic issues.

1) Is my cupsd.conf correct?  I want to access it from any address but restrict access to local users (i.e. users with accounts on the server).

2) After the printer is connected, do I need to add it in the cups web interface on the server for it to be available to clients?  I already have, but should I have?

3) How do I get my client (Ubuntu) to see the networked printer?

---

### Post by ubunterooster on 2010-02-25
have you tried to get it through system>administration>printers>install new printer?

---

### Post by Johnny B on 2010-02-25
don't forget to check the cups configuration at 
[http://192.168.1.2:631/](http://192.168.1.2:631/) 
(you may need to subsitute your local ip)

---

### Post by marshmallow1304 on 2010-02-25
> **Johnny B said:**
> don't forget to check the cups configuration

](*,) I thought I'd gone through the configuration quite thoroughly.  But there it was, staring up at me quite innocently, that cursed empty checkbox labeled "Share published printers connected to this system".



Edit: Still have problems, see below.

---

### Post by marshmallow1304 on 2010-02-25
OK, now I'm having authorization problems.  I've tried all sorts of user/pass combinations, but I can't print when AuthType is Basic, only when AuthType is None.  Obviously, that's not acceptable because I've left the server accessible to the whole network.  How do I set up authorization by user/pass?

Here's my new cupsd.conf:```

LogLevel warning
SystemGroup admin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
DefaultAuthType Basic
DefaultEncryption IfRequested
BrowseAddress @LOCAL
BrowseRemoteProtocols CUPS dnssd
<Location />
  # Allow shared printing and remote administration...
  AuthType Default
  Allow from @LOCAL
  Require valid-user
  Order allow,deny
</Location>
<Location /admin>
  # Allow remote administration...
  AuthType Default
  Allow from @LOCAL
  Require group admin
  Order allow,deny
</Location>
<Location /admin/conf>
  # Allow remote access to the configuration files...
  AuthType Default
  Allow from @LOCAL
  Require group admin
  Order allow,deny
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

---

