---
title: "Printer sharing with cups between two linux computers"
date: 2012-07-20
forum: General Help
---

### Post by DARKAD on 2012-07-20
I'd like to share the usb printer from ubuntu 10.10 192.168.1.128 to the other linux pinguy computer on the lan 192.168.1.129.

this is the configuration file:

LogLevel debug
MaxLogSize 1m
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

this is what I read if I invoke the print job from the ubuntu computer:


D [20/Jul/2012:17:05:15 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:05:15 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.128:631
D [20/Jul/2012:17:05:15 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:05:15 +0200] cupsdNetIFUpdate: "eth0" = fe80::211:d8ff:fea5:3ef0%eth0:631
D [20/Jul/2012:17:05:15 +0200] Report: clients=1
D [20/Jul/2012:17:05:15 +0200] Report: jobs=176
D [20/Jul/2012:17:05:15 +0200] Report: jobs-active=25
D [20/Jul/2012:17:05:15 +0200] Report: printers=2
D [20/Jul/2012:17:05:15 +0200] Report: printers-implicit=0
D [20/Jul/2012:17:05:15 +0200] Report: stringpool-string-count=3506
D [20/Jul/2012:17:05:15 +0200] Report: stringpool-alloc-bytes=7944
D [20/Jul/2012:17:05:15 +0200] Report: stringpool-total-bytes=77616
D [20/Jul/2012:17:05:17 +0200] cupsdReadClient: 12 WAITING Closing on EOF
D [20/Jul/2012:17:05:17 +0200] cupsdCloseClient: 12
D [20/Jul/2012:17:06:10 +0200] cupsdAcceptClient: 12 from localhost:631 (IPv6)
D [20/Jul/2012:17:06:10 +0200] cupsdReadClient: 12 GET /admin/log/error_log HTTP/1.1
D [20/Jul/2012:17:06:10 +0200] cupsdSetBusyState: Active clients
D [20/Jul/2012:17:06:10 +0200] cupsdAuthorize: Authorized as nasone using Basic
D [20/Jul/2012:17:06:10 +0200] cupsdSetBusyState: Not busy
D [20/Jul/2012:17:06:17 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:06:17 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.128:631
D [20/Jul/2012:17:06:17 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:06:17 +0200] cupsdNetIFUpdate: "eth0" = fe80::211:d8ff:fea5:3ef0%eth0:631
D [20/Jul/2012:17:06:17 +0200] Report: clients=1
D [20/Jul/2012:17:06:17 +0200] Report: jobs=176
D [20/Jul/2012:17:06:17 +0200] Report: jobs-active=25
D [20/Jul/2012:17:06:17 +0200] Report: printers=2
D [20/Jul/2012:17:06:17 +0200] Report: printers-implicit=0
D [20/Jul/2012:17:06:17 +0200] Report: stringpool-string-count=3506
D [20/Jul/2012:17:06:17 +0200] Report: stringpool-alloc-bytes=7944
D [20/Jul/2012:17:06:17 +0200] Report: stringpool-total-bytes=77616
D [20/Jul/2012:17:06:40 +0200] cupsdReadClient: 12 WAITING Closing on EOF
D [20/Jul/2012:17:06:40 +0200] cupsdCloseClient: 12
D [20/Jul/2012:17:06:50 +0200] cupsdAcceptClient: 12 from localhost:631 (IPv6)
D [20/Jul/2012:17:06:50 +0200] cupsdReadClient: 12 GET /admin/log/error_log HTTP/1.1
D [20/Jul/2012:17:06:50 +0200] cupsdSetBusyState: Active clients
D [20/Jul/2012:17:06:50 +0200] cupsdAuthorize: Authorized as nasone using Basic
D [20/Jul/2012:17:06:50 +0200] cupsdSetBusyState: Not busy
D [20/Jul/2012:17:07:08 +0200] cupsdReadClient: 12 GET /admin/log/error_log HTTP/1.1
D [20/Jul/2012:17:07:08 +0200] cupsdSetBusyState: Active clients
D [20/Jul/2012:17:07:09 +0200] cupsdAuthorize: Authorized as nasone using Basic
D [20/Jul/2012:17:07:09 +0200] cupsdSetBusyState: Not busy
D [20/Jul/2012:17:07:19 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:07:19 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.128:631
D [20/Jul/2012:17:07:19 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:07:19 +0200] cupsdNetIFUpdate: "eth0" = fe80::211:d8ff:fea5:3ef0%eth0:631
D [20/Jul/2012:17:07:19 +0200] Report: clients=1
D [20/Jul/2012:17:07:19 +0200] Report: jobs=176
D [20/Jul/2012:17:07:19 +0200] Report: jobs-active=25
D [20/Jul/2012:17:07:19 +0200] Report: printers=2
D [20/Jul/2012:17:07:19 +0200] Report: printers-implicit=0
D [20/Jul/2012:17:07:19 +0200] Report: stringpool-string-count=3506
D [20/Jul/2012:17:07:19 +0200] Report: stringpool-alloc-bytes=7944
D [20/Jul/2012:17:07:19 +0200] Report: stringpool-total-bytes=77616
D [20/Jul/2012:17:07:39 +0200] cupsdReadClient: 12 WAITING Closing on EOF
D [20/Jul/2012:17:07:39 +0200] cupsdCloseClient: 12
D [20/Jul/2012:17:07:39 +0200] cupsdAcceptClient: 12 from localhost:631 (IPv4)
D [20/Jul/2012:17:07:39 +0200] cupsdReadClient: 12 GET /admin/log/access_log HTTP/1.1
D [20/Jul/2012:17:07:39 +0200] cupsdSetBusyState: Active clients
D [20/Jul/2012:17:07:39 +0200] cupsdAuthorize: Authorized as nasone using Basic
D [20/Jul/2012:17:07:39 +0200] cupsdSetBusyState: Not busy
D [20/Jul/2012:17:07:39 +0200] cupsdReadClient: 12 WAITING Closing on EOF
D [20/Jul/2012:17:07:39 +0200] cupsdCloseClient: 12
D [20/Jul/2012:17:07:42 +0200] cupsdAcceptClient: 12 from localhost:631 (IPv4)
D [20/Jul/2012:17:07:42 +0200] cupsdReadClient: 12 GET /admin/log/access_log HTTP/1.1
D [20/Jul/2012:17:07:42 +0200] cupsdSetBusyState: Active clients
D [20/Jul/2012:17:07:42 +0200] cupsdAuthorize: Authorized as nasone using Basic
D [20/Jul/2012:17:07:42 +0200] cupsdSetBusyState: Not busy
D [20/Jul/2012:17:07:46 +0200] cupsdReadClient: 12 GET /admin/log/access_log HTTP/1.1
D [20/Jul/2012:17:07:46 +0200] cupsdSetBusyState: Active clients
D [20/Jul/2012:17:07:46 +0200] cupsdAuthorize: Authorized as nasone using Basic
D [20/Jul/2012:17:07:46 +0200] cupsdSetBusyState: Not busy
D [20/Jul/2012:17:08:16 +0200] cupsdReadClient: 12 WAITING Closing on EOF
D [20/Jul/2012:17:08:16 +0200] cupsdCloseClient: 12
D [20/Jul/2012:17:08:21 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:08:21 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.128:631
D [20/Jul/2012:17:08:21 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:08:21 +0200] cupsdNetIFUpdate: "eth0" = fe80::211:d8ff:fea5:3ef0%eth0:631
D [20/Jul/2012:17:08:21 +0200] Report: clients=0
D [20/Jul/2012:17:08:21 +0200] Report: jobs=176
D [20/Jul/2012:17:08:21 +0200] Report: jobs-active=25
D [20/Jul/2012:17:08:21 +0200] Report: printers=2
D [20/Jul/2012:17:08:21 +0200] Report: printers-implicit=0
D [20/Jul/2012:17:08:21 +0200] Report: stringpool-string-count=3506
D [20/Jul/2012:17:08:21 +0200] Report: stringpool-alloc-bytes=7944
D [20/Jul/2012:17:08:21 +0200] Report: stringpool-total-bytes=77616
D [20/Jul/2012:17:09:23 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:09:23 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.128:631
D [20/Jul/2012:17:09:23 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:09:23 +0200] cupsdNetIFUpdate: "eth0" = fe80::211:d8ff:fea5:3ef0%eth0:631
D [20/Jul/2012:17:09:23 +0200] Report: clients=0
D [20/Jul/2012:17:09:23 +0200] Report: jobs=176
D [20/Jul/2012:17:09:23 +0200] Report: jobs-active=25
D [20/Jul/2012:17:09:23 +0200] Report: printers=2
D [20/Jul/2012:17:09:23 +0200] Report: printers-implicit=0
D [20/Jul/2012:17:09:23 +0200] Report: stringpool-string-count=3506
D [20/Jul/2012:17:09:23 +0200] Report: stringpool-alloc-bytes=7944
D [20/Jul/2012:17:09:23 +0200] Report: stringpool-total-bytes=77616
D [20/Jul/2012:17:10:19 +0200] cupsdAcceptClient: 12 from localhost:631 (IPv4)
D [20/Jul/2012:17:10:19 +0200] cupsdReadClient: 12 GET /admin/log/access_log HTTP/1.1
D [20/Jul/2012:17:10:19 +0200] cupsdSetBusyState: Active clients
D [20/Jul/2012:17:10:19 +0200] cupsdAuthorize: Authorized as nasone using Basic
D [20/Jul/2012:17:10:19 +0200] cupsdSetBusyState: Not busy
D [20/Jul/2012:17:10:25 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:10:25 +0200] cupsdNetIFUpdate: "eth0" = 192.168.1.128:631
D [20/Jul/2012:17:10:25 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [20/Jul/2012:17:10:25 +0200] cupsdNetIFUpdate: "eth0" = fe80::211:d8ff:fea5:3ef0%eth0:631
D [20/Jul/2012:17:10:25 +0200] Report: clients=1
D [20/Jul/2012:17:10:25 +0200] Report: jobs=176
D [20/Jul/2012:17:10:25 +0200] Report: jobs-active=25
D [20/Jul/2012:17:10:25 +0200] Report: printers=2
D [20/Jul/2012:17:10:25 +0200] Report: printers-implicit=0
D [20/Jul/2012:17:10:25 +0200] Report: stringpool-string-count=3506
D [20/Jul/2012:17:10:25 +0200] Report: stringpool-alloc-bytes=7944
D [20/Jul/2012:17:10:25 +0200] Report: stringpool-total-bytes=77616
D [20/Jul/2012:17:10:27 +0200] cupsdReadClient: 12 GET /admin/log/error_log HTTP/1.1
D [20/Jul/2012:17:10:27 +0200] cupsdSetBusyState: Active clients
D [20/Jul/2012:17:10:27 +0200] cupsdAuthorize: Authorized as nasone using Basic

It tries many time to do the job , with no result.

From the ubuntu cups 127.0.0.1:631 access_log there are no messages.

What can I do?

---

### Post by Cheesehead on 2012-07-20
Here's how I solved this problem. It's cumulative; when one step breaks, that's what needs to be fixed before moving on...

1) Make sure the printer is turned on and hooked up.

2) On the SERVER (Ubuntu 10.10 192.168.1.128 ), make sure CUPS is running (ps -e).

3) On the SERVER, open the CUPS printer web page
( [http://localhost:631/printers/](http://localhost:631/printers/) ) and make sure the printer is listed.

4) On the SERVER, try a test print to make sure the printer config is
set up properly.

5) On the SERVER, open the CUPS admin web page
( [http://localhost:631/admin](http://localhost:631/admin) ) and make sure that the checkbox "Share
printers connected to this system" is checked.

6) On the CLIENT (pinguy 192.168.1.129), make sure cups is running (ps -e ).

7) On the CLIENT, open the CUPS admin web page
( [http://localhost:631/admin](http://localhost:631/admin) ) and make sure that the checkbox "Show
printers shared by other systems" is checked.

8 ) On the CLIENT, open the CUPS printer web page
( [http://localhost:631/printers/](http://localhost:631/printers/) ) and make sure the printer is listed.

9) On the CLIENT, try a test print.

---

### Post by DARKAD on 2012-07-20
Thanks.
It was necessary to set cups on the client machine too, and everything works.
When I usually set a server daemon on a pc, I don't have to set another daemon to make the first works.
But sometime this is the evil linux world!

---

