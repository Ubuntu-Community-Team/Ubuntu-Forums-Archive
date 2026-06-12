---
title: "Problems printing from Windows clients to Lucid Lynx 10.04"
date: 2010-07-17
forum: General Help
---

### Post by jwyeo2 on 2010-07-17
[SIZE=3]I'm having problems printing from Windows to shared printers on Ubuntu 10.04. 

Installed Ubuntu 10.04 in early June and applied updates. 
Setup print sharing via System -> Administration -> Printing as outlined in several places on the 'net. 
Printers are an HP LJ 1012 and a Epson Workforce 500. 
Configured my Windows clients (XP & 7) to print via [http://server:631/printers/printer-name](http://server:631/printers/printer-name).
Everything worked like a charm. Easiest Linux install and setup ever. Sweet!

Several weeks later the Windows clients would no longer print. There was a system update sometime prior to this but I'm not sure of the date or even if that was the problem. I tried deleting the printers from Windows and adding them again but received errors that it could not connect to the printer.  I tried a bunch of things and eventually discovered that printing via Samba print shares (\\server\printer-name) worked. Printing from Windows slower now but I could live with it. 

A few weeks later the Windows XP clients were unable to print again. I tried a bunch more things and realized that the HP printer wasn't working from Ubuntu. I updated the URL of the HP printer from the HP:// scheme to the usb:// as mentioned elsewhere in the forums. Printing from Ubuntu is fine. The Windows XP boxes were still unable to print to either printer. The CUPS http address was still not working on any Windows machine. 

Any ideas on how to fix this? Ideally I would be able to go back to specifying the CUPS address (http) from the Windows clients. 

I've attached my cupsd.conf. Let me know if anything else would be helpful. 

Thanks, 

Jeff
[/SIZE]
```

# cupsd.conf
LogLevel warn
MaxLogSize 0
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
ServerName *
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
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
  <Limit CUPS-Authenticate-Job>
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

