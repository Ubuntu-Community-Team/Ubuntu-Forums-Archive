---
title: "Cups printing between Ubuntu and Mac osx"
date: 2010-05-06
forum: General Help
---

### Post by waloshin on 2010-05-06
i am running ubuntu server with Cups installed I have my Samsung Ml 1610 printer working, but it wont work on Mac osx. I share the printer through the ip address 192.168.2.4:631

Is there anything I am missing?

Printer sharing is enabled on ubuntu.

Error: 

[-0600] Unable to encrypt connection from 192.168.2.2(My macbook) - A record packet with illegal version was received.

---

### Post by waloshin on 2010-05-06
Here is the config file:

```
LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
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
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
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
      AuthType Default
      Require user @OWNER @SYSTEM
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>
```

---

### Post by alek66 on 2010-05-09
I have the same problem here... funny thing on older versions used to work perfect

---

### Post by cleanthes on 2010-05-21
Danger! Danger! I don't know enough about CUPS, but I did have this same problem, and have fixed it by editing this line:
  <Limit Create-Job Print-Job Print-URI>

To read:
  <Limit Create-Job Print-URI>

i.e. remove 'Print-Job'

This is in a section defining authentication requirements. I think this is saying "require authentication for Print-Jon". If you look in your /var/log/cups/error_log you'll see errors relating to authentication when you try to print from OSX.

I removed 'Print-Job' and can now print OK.

(btw, I did also have to configure the OSX settings using its own CUPS interface: setup the printer on OSX with whatever settings you can, then go to [http://localhost:631/](http://localhost:631/) *on the Mac*, find your printer and set it to use Internet Printing Protocol (HTTP).)

Good luck! And remember, this may not be a good, proper or permanent fix!

---

### Post by alek66 on 2010-05-21
> **cleanthes said:**
> Danger! Danger! I don't know enough about CUPS, but I did have this same problem, and have fixed it by editing this line:
  <Limit Create-Job Print-Job Print-URI>

To read:
  <Limit Create-Job Print-URI>

i.e. remove 'Print-Job'

This is in a section defining authentication requirements. I think this is saying "require authentication for Print-Jon". If you look in your /var/log/cups/error_log you'll see errors relating to authentication when you try to print from OSX.

I removed 'Print-Job' and can now print OK.

(btw, I did also have to configure the OSX settings using its own CUPS interface: setup the printer on OSX with whatever settings you can, then go to [http://localhost:631/](http://localhost:631/) *on the Mac*, find your printer and set it to use Internet Printing Protocol (HTTP).)

Good luck! And remember, this may not be a good, proper or permanent fix!

Where do I edit that?

---

### Post by waloshin on 2010-05-21
Thanks, and I would guess in the cups .conf file.

---

