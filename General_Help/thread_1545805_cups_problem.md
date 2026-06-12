---
title: "cups problem?"
date: 2010-08-04
forum: General Help
---

### Post by macadamianuts on 2010-08-04
Hi everybody.
I have a problem with cups. Until not long ago my hp deskjet f2140 was working fine. After a recent update printing started not working.

I think I reinstalled all the reinstallable, including cups and hplip. Still nothing. Also read many threads, but nothing really relevant.

Description:
-- cups is reported as running
-- The printer is recognised and "ready to print".
-- When I try to access localhost:631 nothing happens (firefox loads an empty page, but no error is given. No authorization is requested for 631 nor for 631/admin. Authorization is requested for 631/admin/conf. After accessing, white page again)
-- Jobs are stopped almost instantaneously. At the end of the thread you'll find the output of the diagnosis tool.
-- cups.conf seems to be ok (and newly reinstalled!):

Any idea? (ubuntu 8.4 on asus laptop)
Thank you very much!

---------------------------------------------------------------------
cups.conf:

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

----------------------------------------------------------------
Diagnosis tool output: attached

---

### Post by utilitytrack on 2010-08-04
Hello, 
> Any idea?
 upgrade to 10.04

---

### Post by macadamianuts on 2010-08-04
```

oops, for some reason the diagnosis output is consedered too long to be attached!
here you are:
---------------------------------------------------------------
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Deskjet-F2100-series>,
 'cups_instance': None,
 'cups_queue': 'Deskjet-F2100-series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/Deskjet_F2100_series?serial=CN78E4Q06T04TK',
                       'printer-info': u'HP Deskjet F2100 series',
                       'printer-is-shared': True,
                       'printer-location': u'fausto-laptop',
                       'printer-make-and-model': u'HP Deskjet f2100 series Foomatic/hpijs, hpijs 2.8.7',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 36876,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Deskjet-F2100-series'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 2.8.7)\x1b[0m',
                   '\x1b[01mSystem Tray Status Service ver. 0.1\x1b[0m',
                   '',
                   'Copyright (c) 2001-8 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 2.8.7)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 4.1\x1b[0m',
                   '',
                   'Copyright (c) 2001-8 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/usb/Deskjet_F2100_series?serial=CN78E4Q06T04TK\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  agent1-ack                    False                                                     ',
                   '  agent1-desc                   Black cartridge                                           ',
                   '  agent1-dvc                    0                                                         ',
                   '  agent1-health                 0                                                         ',
                   '  agent1-health-desc            Good/OK                                                   ',
                   '  agent1-hp-ink                 False                                                     ',
                   '  agent1-id                     0                                                         ',
                   '  agent1-kind                   3                                                         ',
                   '  agent1-known                  False                                                     ',
                   '  agent1-level                  0                                                         ',
                   '  agent1-level-trigger          0                                                         ',
                   '  agent1-sku                    21(C9153A)                                                ',
                   '  agent1-type                   1                                                         ',
                   '  agent1-virgin                 False                                                     ',
                   '  agent2-ack                    False                                                     ',
                   '  agent2-desc                   Tri-color cartridge                                       ',
                   '  agent2-dvc                    0                                                         ',
                   '  agent2-health                 0                                                         ',
                   '  agent2-health-desc            Good/OK                                                   ',
                   '  agent2-hp-ink                 False                                                     ',
                   '  agent2-id                     0                                                         ',
                   '  agent2-kind                   3                                                         ',
                   '  agent2-known                  False                                                     ',
                   '  agent2-level                  9                                                         ',
                   '  agent2-level-trigger          0                                                         ',
                   '  agent2-sku                    22(C9352A)                                                ',
                   '  agent2-type                   2                                                         ',
                   '  agent2-virgin                 False                                                     ',
                   '  back-end                      hp                                                        ',
                   '  cups-printer                  Deskjet-F2100-series                                      ',
                   '  cups-uri                      hp:/usb/Deskjet_F2100_series?serial=CN78E4Q06T04TK        ',
                   '  dev-file                                                                                ',
                   '  device-state                  1                                                         ',
                   '  device-uri                    hp:/usb/Deskjet_F2100_series?serial=CN78E4Q06T04TK        ',
                   '  deviceid                      MFG:HP;MDL:Deskjet F2100                                  ',
                   '                                series;CMD:LDL,MLC,PML,DYN;CLS:PRINTER;1284.4DL:4d,4e,1;SN',
                   '                                :CN78E4Q06T04TK;S:0380008000020020002c1480000c2500009;Z:00',
                   '                                7,0A20000;                                                ',
                   '  duplexer                      0                                                         ',
                   '  error-state                   0                                                         ',
                   '  host                                                                                    ',
                   '  in-tray1                      True                                                      ',
                   '  in-tray2                      False                                                     ',
                   '  is-hp                         True                                                      ',
                   '  media-path                    2                                                         ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  photo-tray                    0                                                         ',
                   '  port                          1                                                         ',
                   '  r                             0                                                         ',
                   '  revision                      3                                                         ',
                   '  rg                            000                                                       ',
                   '  rr                            000000                                                    ',
                   '  rs                            000000000                                                 ',
                   '  scan-uri                      hpaio:/usb/Deskjet_F2100_series?serial=CN78E4Q06T04TK     ',
                   '  serial                        CN78E4Q06T04TK                                            ',
                   '  status-code                   1000                                                      ',
                   '  status-desc                   Idle.                                                     ',
                   '  supply-door                   0                                                         ',
                   '  top-door                      1                                                         ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    5                                                         ',
                   '  clean-type                    2                                                         ',
                   '  color-cal-type                0                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          0                                                         ',
                   '  fax-type                      0                                                         ',
                   '  fw-download                   0                                                         ',
                   '  icon                          psc_1100_series.png                                       ',
                   '  io-mfp-mode                   6                                                         ',
                   '  io-mode                       1                                                         ',
                   '  io-support                    2                                                         ',
                   '  job-storage                   0                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         Deskjet_F2100_series                                      ',
                   '  model-ui                      HP Deskjet f2100 series                                   ',
                   '  model1                        Deskjet F2120 All-in-One                                  ',
                   '  model2                        Deskjet F2128 All-in-One                                  ',
                   '  model3                        Deskjet F2140 All-in-One                                  ',
                   '  model4                        Deskjet F2180 All-in-One                                  ',
                   '  model5                        Deskjet F2187 All-in-One                                  ',
                   '  model6                        Deskjet F2188 All-in-One                                  ',
                   '  model7                        Deskjet F2179 All-in-One                                  ',
                   '  model8                        Deskjet F2110 All-in-One                                  ',
                   '  model9                        Deskjet F2185 All-in-One                                  ',
                   '  panel-check-type              0                                                         ',
                   '  pcard-type                    0                                                         ',
                   '  plugin                        0                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        1                                                         ',
                   '  r0-agent1-kind                3                                                         ',
                   '  r0-agent1-sku                 21(C9153A)                                                ',
                   '  r0-agent1-type                1                                                         ',
                   '  r0-agent2-kind                3                                                         ',
                   '  r0-agent2-sku                 22(C9352A)                                                ',
                   '  r0-agent2-type                2                                                         ',
                   '  r1-agent1-kind                3                                                         ',
                   '  r1-agent1-sku                 21(C9351A)                                                ',
                   '  r1-agent1-type                1                                                         ',
                   '  r1-agent2-kind                3                                                         ',
                   '  r1-agent2-sku                 22(C9352A)                                                ',
                   '  r1-agent2-type                2                                                         ',
                   '  r2-agent1-kind                3                                                         ',
                   '  r2-agent1-sku                 21 (C9351A)                                               ',
                   '  r2-agent1-type                1                                                         ',
                   '  r2-agent2-kind                3                                                         ',
                   '  r2-agent2-sku                 22 (C9352A)                                               ',
                   '  r2-agent2-type                2                                                         ',
                   '  r3-agent1-kind                3                                                         ',
                   '  r3-agent1-sku                 21 (C9351A)                                               ',
                   '  r3-agent1-type                1                                                         ',
                   '  r3-agent2-kind                3                                                         ',
                   '  r3-agent2-sku                 22 (C9352A)                                               ',
                   '  r3-agent2-type                2                                                         ',
                   '  r4-agent1-kind                3                                                         ',
                   '  r4-agent1-sku                 21 (C9351A)                                               ',
                   '  r4-agent1-type                1                                                         ',
                   '  r4-agent2-kind                3                                                         ',
                   '  r4-agent2-sku                 22 (C9352A)                                               ',
                   '  r4-agent2-type                2                                                         ',
                   '  r5-agent1-kind                3                                                         ',
                   '  r5-agent1-sku                 21 (C9351A)                                               ',
                   '  r5-agent1-type                1                                                         ',
                   '  r5-agent2-kind                3                                                         ',
                   '  r5-agent2-sku                 22 (C9352A)                                               ',
                   '  r5-agent2-type                2                                                         ',
                   '  r6-agent1-kind                3                                                         ',
                   '  r6-agent1-sku                 21 (C9351A)                                               ',
                   '  r6-agent1-type                1                                                         ',
                   '  r6-agent2-kind                3                                                         ',
                   '  r6-agent2-sku                 22 (C9352A)                                               ',
                   '  r6-agent2-type                2                                                         ',
                   '  r7-agent1-kind                3                                                         ',
                   '  r7-agent1-sku                 816 (C8816A/B)                                            ',
                   '  r7-agent1-type                1                                                         ',
                   '  r7-agent2-kind                3                                                         ',
                   '  r7-agent2-sku                 817 (C8817A/C8817G)                                       ',
                   '  r7-agent2-type                2                                                         ',
                   '  r816-agent1-kind              3                                                         ',
                   '  r816-agent1-sku                                                                         ',
                   '  r816-agent1-type              1                                                         ',
                   '  r816-agent2-kind              3                                                         ',
                   '  r816-agent2-sku                                                                         ',
                   '  r816-agent2-type              2                                                         ',
                   '  scan-style                    1                                                         ',
                   '  scan-type                     1                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       0                                                         ',
                   '  status-type                   2                                                         ',
                   '  support-released              1                                                         ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   1.7.4                                                     ',
                   "  tech-class                    ['DJ3320']                                                ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     2                                                         ',
                   '  usb-pid                       7d04                                                      ',
                   '  usb-vid                       03f0                                                      ',
                   '',
                   'Done.',
                   ''],
                  ['']),
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:HP;MDL:Deskjet F2100 series;CLS:PRINTER;DES:Deskjet F2100 series;SN:CN78E4Q06T04TK;',
                      'device-info': u'HP Deskjet F2100 series USB CN78E4Q06T04TK HPLIP',
                      'device-make-and-model': u'HP Deskjet F2100 series'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
 'printer-state-reasons': [u'connecting-to-device']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 3301L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_job_status': [(True,
                           1,
                           'Deskjet-F2100-series',
                           'Stoch-Version2.pdf',
                           'Stopped',
                           {'PageSize': u'Letter',
                            'PrintoutMode': u'Draft.Gray',
                            'Quality': u'FromPrintoutMode',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-ca',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 1,
                            'job-k-octets': 2139,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/1',
                            'job-name': u'Stoch-Version2.pdf',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'fausto',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'connecting-to-device'],
                            'job-printer-up-time': 1280934990,
                            'job-printer-uri': u'ipp://fausto-laptop:631/printers/Deskjet-F2100-series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/1',
                            'job-uuid': u'urn:uuid:f2706852-f863-30db-5361-e2124acafdae',
                            'number-up': 1,
                            'number-up-layout': u'lrtb',
                            'printer-uri': u'ipp://localhost:631/printers/Deskjet-F2100-series',
                            'time-at-completed': None,
                            'time-at-creation': 1280934944,
                            'time-at-processing': 1280934944})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [04/Aug/2010:15:16:19 +0000] cupsdCloseClient: 7',
               'D [04/Aug/2010:15:16:19 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [04/Aug/2010:15:16:19 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [04/Aug/2010:15:16:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [04/Aug/2010:15:16:19 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [04/Aug/2010:15:16:19 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [04/Aug/2010:15:16:19 +0000] cupsdCloseClient: 7',
               'D [04/Aug/2010:15:16:19 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [04/Aug/2010:15:16:19 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [04/Aug/2010:15:16:19 +0000] cupsdAuthorize: No authentication data provided.',
               'D [04/Aug/2010:15:16:19 +0000] Create-Printer-Subscription /',
               'D [04/Aug/2010:15:16:19 +0000] cupsdCreateSubscription(con=0xb8b77f98(7), uri="/")',
               'D [04/Aug/2010:15:16:19 +0000] pullmethod="ippget"',
               'D [04/Aug/2010:15:16:19 +0000] notify-lease-duration=86400',
               'D [04/Aug/2010:15:16:19 +0000] notify-time-interval=0',
               'D [04/Aug/2010:15:16:19 +0000] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [04/Aug/2010:15:16:19 +0000] Added subscription 135 for server',
               'I [04/Aug/2010:15:16:19 +0000] Saving subscriptions.conf...',
               'D [04/Aug/2010:15:16:19 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [04/Aug/2010:15:16:19 +0000] cupsdCloseClient: 7',
               'D [04/Aug/2010:15:16:20 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [04/Aug/2010:15:16:20 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [04/Aug/2010:15:16:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [04/Aug/2010:15:16:20 +0000] Get-Notifications /',
               'D [04/Aug/2010:15:16:20 +0000] cupsdIsAuthorized: requesting-user-name="fausto"',
               'D [04/Aug/2010:15:16:20 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [04/Aug/2010:15:16:20 +0000] cupsdCloseClient: 7',
               'D [04/Aug/2010:15:16:30 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [04/Aug/2010:15:16:30 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [04/Aug/2010:15:16:30 +0000] cupsdAuthorize: No authentication data provided.',
               'D [04/Aug/2010:15:16:30 +0000] Get-Job-Attributes ipp://localhost/jobs/1',
               'D [04/Aug/2010:15:16:30 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [04/Aug/2010:15:16:30 +0000] cupsdCloseClient: 7',
               'D [04/Aug/2010:15:16:30 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [04/Aug/2010:15:16:30 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [04/Aug/2010:15:16:30 +0000] cupsdAuthorize: No authentication data provided.',
               'D [04/Aug/2010:15:16:30 +0000] Cancel-Subscription /',
               'D [04/Aug/2010:15:16:30 +0000] cupsdIsAuthorized: requesting-user-name="fausto"',
               'I [04/Aug/2010:15:16:30 +0000] Saving subscriptions.conf...',
               'D [04/Aug/2010:15:16:30 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [04/Aug/2010:15:16:30 +0000] cupsdCloseClient: 7',
               'D [04/Aug/2010:15:16:30 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [04/Aug/2010:15:16:30 +0000] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1',
               'D [04/Aug/2010:15:16:30 +0000] cupsdAuthorize: No authentication data provided.']}

```

---

### Post by utilitytrack on 2010-08-04
please use [CODE] tag for long outputs

---

### Post by macadamianuts on 2010-08-04
> **utilitytrack said:**
> Hello, 
 upgrade to 10.04

well, that might be, but doesn't need to be, a solution as other problems could arise.
A few weeks ago I tried the 10.04 live cd: black screen.
However, I would really like to avoid an upgrade or postpone it to when I'll have more time. 
Thanks, anyways.

---

### Post by utilitytrack on 2010-08-04
Ok, don't be mad at me but you understand that Ubuntu 8.04 Hardy it's really bad? :) Why you got black screen when tried install 10.04 is a great separate question. Your words about to avoid a upgrade until you have enough time it's very right think, though.


Please give here [FONT='Courier New']dpkg -l *cups*[/FONT]
[FONT='Courier New']
[/FONT]

---

### Post by macadamianuts on 2010-08-05
> **utilitytrack said:**
> Ok, don't be mad at me but you understand that Ubuntu 8.04 Hardy it's really bad? :) Why you got black screen when tried install 10.04 is a great separate question. Your words about to avoid a upgrade until you have enough time it's very right think, though.


Please give here [FONT='Courier New']dpkg -l *cups*[/FONT]
[FONT='Courier New']
[/FONT]

8.04 is not so bad, actually! :)
and I'm not mad at all.
here you are:

sudo dpkg -l *cups*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                  Version                               Description
+++-=====================================-=====================================-==========================================================================================
ii  bluez-cups                            4.12-0ubuntu5                         Bluetooth printer driver for CUPS
ii  cups                                  1.3.9-2ubuntu9.5                      Common UNIX Printing System(tm) - server
ii  cups-bsd                              1.3.9-2ubuntu9.5                      Common UNIX Printing System(tm) - BSD commands
ii  cups-client                           1.3.9-2ubuntu9.5                      Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                           1.3.9-2ubuntu9.5                      Common UNIX Printing System(tm) - common files
un  cups-driver-gimpprint                 <none>                                (no description available)
un  cups-driver-gimpprint-data            <none>                                (no description available)
ii  cups-driver-gutenprint                5.2.0~rc1-0ubuntu1                    printer drivers for CUPS
un  cups-pdf                              <none>                                (no description available)
un  cups-pt                               <none>                                (no description available)
ii  cupsddk                               1.2.3-3                               CUPS Driver Development Kit
ii  cupsddk-drivers                       1.2.3-3                               CUPS Driver Development Kit - Driver files
un  cupsomatic-ppd                        <none>                                (no description available)
pn  cupsys                                <none>                                (no description available)
un  cupsys-bsd                            <none>                                (no description available)
pn  cupsys-client                         <none>                                (no description available)
un  cupsys-common                         <none>                                (no description available)
un  cupsys-driver-gutenprint              <none>                                (no description available)
ii  hal-cups-utils                        0.6.17+git20080728-0ubuntu2           CUPS integration with HAL
ii  libcups2                              1.3.9-2ubuntu9.5                      Common UNIX Printing System(tm) - libs
ii  libcupsimage2                         1.3.9-2ubuntu9.5                      Common UNIX Printing System(tm) - image libs
un  libcupsys2                            <none>                                (no description available)
ii  libgnomecups1.0-1                     0.2.3-2build1                         GNOME library for CUPS interaction
ii  python-cups                           1.9.41-0ubuntu1                       Python bindings for CUPS
ii  python-cupshelpers                    1.0.5+git20080819-0ubuntu6            Python modules for printer configuration with CUPS
un  python2.4-cups                        <none>                                (no description available)
un  python2.5-cups                        <none>                                (no description available)

---

### Post by macadamianuts on 2010-08-06
up!;)

---

### Post by utilitytrack on 2010-08-06
Well, I might say again: I don't see any others simple ways to setting up your CUPS server except update it to last stable. But this related to serious tasks to solve [FONT="Courier New"]aptitude[/FONT] dependencies. So I recommend you to upgrade whole system through [FONT="Courier New"]aptitude update[/FONT] and [FONT="Courier New"]aptitude upgrade[/FONT].

---

