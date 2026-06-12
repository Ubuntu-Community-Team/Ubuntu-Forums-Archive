---
title: "Cups keeps adding printers and disabling the default"
date: 2009-07-27
forum: General Help
---

### Post by martinbaselier on 2009-07-27
The situation:

I have a desktop set up for my dad with ubuntu installed. 

The problem is that it keeps adding his printer. I haven't been able to find out what triggers this event and how to prevent it.

My guess is that this might have something to do with it. 
cat /var/log/cups/error_log
E [27/Jul/2009:13:34:07 +0200] Resume-Printer: Unauthorized
cat /var/log/cups/access_log shows
```

localhost - - [27/Jul/2009:13:34:07 +0200] "POST /admin/ HTTP/1.1" 401 160 Resume-Printer successful-ok
localhost - root [27/Jul/2009:13:34:07 +0200] "POST /admin/ HTTP/1.1" 200 160 Resume-Printer successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 251 Create-Printer-Subscription successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 75 CUPS-Get-Default successful-ok
localhost - - [27/Jul/2009:13:36:24 +0200] "POST / HTTP/1.1" 200 152 Get-Notifications successful-ok
localhost - - [27/Jul/2009:13:36:31 +0200] "POST / HTTP/1.1" 200 151 Cancel-Subscription successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 199 Get-Jobs successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 323 Create-Printer-Subscription successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 220 Get-Jobs successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 222 Get-Printer-Attributes successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 195 Get-Printer-Attributes successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 164 Get-Job-Attributes successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 220 Get-Jobs successful-ok
localhost - - [27/Jul/2009:13:36:35 +0200] "POST / HTTP/1.1" 200 152 Get-Notifications successful-ok

```

As a side effect, it disables the default printer and you need to enable by hand, by going to the printer control panel, right clicking on it and enabling it.

How could I prevent this from happening?

---

### Post by martinbaselier on 2009-07-28
Anyone got a clue what I could test? Maybe someone's got a link providing more info about cups and the processed involved?

---

### Post by martinbaselier on 2009-07-29
This is what my /etc/cups/cupsd.conf looks like:
```

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  Encryption Required
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
    Order allow,deny
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
PreserveJobHistory No

```

---

### Post by martinbaselier on 2009-07-29
*bump*

---

### Post by martinbaselier on 2009-07-31
*bump*

---

### Post by danwood76 on 2009-07-31
What printer is it?
Does it connect over USB?

---

### Post by martinbaselier on 2009-07-31
It's connected via usb. It's a photosmart 7345

---

### Post by martinbaselier on 2009-08-03
*bump*

---

### Post by danwood76 on 2009-08-03
Several things you could try:

Try a different USB port, it could be that the PC is going to sleep or something and disabling certain ports so when it starts up it changes port ID.

Change the drivers your printer Uses, I spotted a couple of drivers that your printer can use so it might be worth trying the other driver:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7345](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7345)

---

