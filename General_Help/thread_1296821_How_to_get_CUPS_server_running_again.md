---
title: "How to get CUPS server running again?"
date: 2009-10-21
forum: General Help
---

### Post by peter_kint on 2009-10-21
Hello,
Printing suddenly became impossible
**Cups server not running**

I checked in System/Services : CUPS is there allright but apparently it's not running??

How can get it running again?

Thx,
PK

---

### Post by wojox on 2009-10-21
Try:

```
sudo /etc/init.d/cupsys start
```

Also look here in a web browser:

```
http://localhost:631/
```

---

### Post by peter_kint on 2009-10-21
> **wojox said:**
> Try:

```
sudo /etc/init.d/cupsys start
```Also look here in a web browser:

```
http://localhost:631/
```

Hi, thx

This is the output:
peter@peter-desktop:~$ sudo /etc/init.d/cupsys start
[sudo] password for peter: 
sudo: /etc/init.d/cupsys: command not found
peter@peter-desktop:~$ [http://localhost:631/](http://localhost:631/)
bash: [http://localhost:631/:](http://localhost:631/:) No such file or directory
peter@peter-desktop:~$ 

I went into synaptic packages and noticed cupsys was not installed (I somehow musthave removed it in the process of installing/removing  Xpdf)

I used troubleshooting in the printing service and this is what I get:
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest DESKJET-840C (default)>,
 'cups_instance': None,
 'cups_queue': 'DESKJET-840C',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/par/DESKJET_840C?device=/dev/parport0',
                       'printer-info': u'HEWLETT-PACKARD DESKJET 840C',
                       'printer-is-shared': True,
                       'printer-location': u'peter-desktop',
                       'printer-make-and-model': u'HP Deskjet 840c hpijs, 3.9.2',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to start backend "hp" - Success.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DESKJET-840C'},
 'cups_printer_remote': False,
 'hplip_output': ([''], ['/bin/sh: hp-info: not found', ''], 127),
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': (['hpijs'], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Printer state reasons):
{'printer-state-message': u'Unable to start backend "hp" - Success.',
 'printer-state-reasons': [u'none']}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 30862L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_job_status': [(True,
                           24,
                           'DESKJET-840C',
                           'brief_btw_directie',
                           'Processing',
                           {'PageSize': u'Letter',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 24,
                            'job-k-octets': 53,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/24',
                            'job-name': u'brief_btw_directie',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'peter',
                            'job-preserved': True,
                            'job-printer-up-time': 1256116080,
                            'job-printer-uri': u'ipp://peter-desktop:631/printers/DESKJET-840C',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/24',
                            'job-uuid': u'urn:uuid:c86962fa-b93d-3687-510d-5a98148f9500',
                            'printer-uri': u'ipp://localhost/printers/DESKJET-840C',
                            'time-at-completed': None,
                            'time-at-creation': 1256115972,
                            'time-at-processing': 1256116069}),
                          (False,
                           22,
                           'DESKJET-840C',
                           'brief_btw_directie',
                           'Processing',
                           None),
                          (False,
                           23,
                           'DESKJET-840C',
                           'Test Page',
                           'Processing',
                           None)],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [21/Oct/2009:11:07:36 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Oct/2009:11:07:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:07:36 +0200] Get-Jobs ipp://localhost/printers/',
               'D [21/Oct/2009:11:07:36 +0200] [Job 22] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 23] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 24] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Oct/2009:11:07:36 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Oct/2009:11:07:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:07:36 +0200] Get-Jobs ipp://localhost/printers/',
               'D [21/Oct/2009:11:07:36 +0200] [Job 1] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 2] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 3] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 4] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 5] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 6] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 7] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 8] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 9] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 10] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 11] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 12] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 13] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 14] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 15] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 16] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 17] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 18] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 19] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 20] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] [Job 21] Loading attributes...',
               'D [21/Oct/2009:11:07:36 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Oct/2009:11:07:36 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Oct/2009:11:07:36 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:07:36 +0200] Create-Printer-Subscription /',
               'D [21/Oct/2009:11:07:36 +0200] cupsdCreateSubscription(con=0xb8960050(8), uri="/")',
               'D [21/Oct/2009:11:07:36 +0200] pullmethod="ippget"',
               'D [21/Oct/2009:11:07:36 +0200] notify-lease-duration=86400',
               'D [21/Oct/2009:11:07:36 +0200] notify-time-interval=0',
               'D [21/Oct/2009:11:07:36 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [21/Oct/2009:11:07:36 +0200] Added subscription 18 for server',
               'I [21/Oct/2009:11:07:36 +0200] Saving subscriptions.conf...',
               'D [21/Oct/2009:11:07:36 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Oct/2009:11:07:37 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Oct/2009:11:07:37 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:07:37 +0200] Get-Notifications /',
               'D [21/Oct/2009:11:07:37 +0200] cupsdIsAuthorized: requesting-user-name="peter"',
               'D [21/Oct/2009:11:07:37 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] job-sheets=none,none',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] banner_page = 0',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] argv[0]="DESKJET-840C"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] argv[1]="22"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] argv[2]="peter"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] argv[3]="brief_btw_directie"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] argv[4]="1"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] argv[5]="PageSize=Letter job-uuid=urn:uuid:ad12f626-5ce0-37ad-5914-1614f48acf02"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] argv[6]="/var/spool/cups/d00022-001"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[9]="SERVER_ADMIN=root@peter-desktop"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[12]="TZ=Europe/Paris"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[13]="USER=root"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[16]="IPP_PORT=631"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[17]="CHARSET=utf-8"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[18]="LANG=en_US.UTF8"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[19]="PPD=/etc/cups/ppd/DESKJET-840C.ppd"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[20]="RIP_MAX_CACHE=8m"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[22]="DEVICE_URI=hp:/par/DESKJET_840C?device=/dev/parport0"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[23]="PRINTER=DESKJET-840C"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 22] envp[24]="FINAL_CONTENT_TYPE=printer/DESKJET-840C"',
               'I [21/Oct/2009:11:07:49 +0200] [Job 22] Started filter /usr/lib/cups/filter/pstopdf (PID 4065)',
               'I [21/Oct/2009:11:07:49 +0200] [Job 22] Started filter /usr/lib/cups/filter/pdftopdf (PID 4066)',
               'I [21/Oct/2009:11:07:49 +0200] [Job 22] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4068)',
               'E [21/Oct/2009:11:07:49 +0200] Unable to execute /usr/lib/cups/backend/hp: No such file or directory',
               'E [21/Oct/2009:11:07:49 +0200] [Job 22] Unable to start backend "hp" - Success.',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] job-sheets=none,none',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] banner_page = 0',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] argv[0]="DESKJET-840C"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] argv[1]="23"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] argv[2]="peter"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] argv[3]="Test Page"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] argv[4]="1"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] argv[5]="job-uuid=urn:uuid:957e8503-d2ca-3fa9-40c9-89d8f66ec998"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] argv[6]="/var/spool/cups/d00023-001"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[9]="SERVER_ADMIN=root@peter-desktop"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[12]="TZ=Europe/Paris"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[13]="USER=root"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[16]="IPP_PORT=631"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[17]="CHARSET=utf-8"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[18]="LANG=en_US.UTF8"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[19]="PPD=/etc/cups/ppd/DESKJET-840C.ppd"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[20]="RIP_MAX_CACHE=8m"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[22]="DEVICE_URI=hp:/par/DESKJET_840C?device=/dev/parport0"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[23]="PRINTER=DESKJET-840C"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 23] envp[24]="FINAL_CONTENT_TYPE=printer/DESKJET-840C"',
               'I [21/Oct/2009:11:07:49 +0200] [Job 23] Started filter /usr/lib/cups/filter/pstopdf (PID 4070)',
               'I [21/Oct/2009:11:07:49 +0200] [Job 23] Started filter /usr/lib/cups/filter/pdftopdf (PID 4072)',
               'I [21/Oct/2009:11:07:49 +0200] [Job 23] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4074)',
               'E [21/Oct/2009:11:07:49 +0200] Unable to execute /usr/lib/cups/backend/hp: No such file or directory',
               'E [21/Oct/2009:11:07:49 +0200] [Job 23] Unable to start backend "hp" - Success.',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] job-sheets=none,none',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] banner_page = 0',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] argv[0]="DESKJET-840C"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] argv[1]="24"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] argv[2]="peter"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] argv[3]="brief_btw_directie"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] argv[4]="1"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] argv[5]="PageSize=Letter job-uuid=urn:uuid:c86962fa-b93d-3687-510d-5a98148f9500"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] argv[6]="/var/spool/cups/d00024-001"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[9]="SERVER_ADMIN=root@peter-desktop"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[12]="TZ=Europe/Paris"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[13]="USER=root"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[16]="IPP_PORT=631"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[17]="CHARSET=utf-8"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[18]="LANG=en_US.UTF8"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[19]="PPD=/etc/cups/ppd/DESKJET-840C.ppd"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[20]="RIP_MAX_CACHE=8m"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[22]="DEVICE_URI=hp:/par/DESKJET_840C?device=/dev/parport0"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[23]="PRINTER=DESKJET-840C"',
               'D [21/Oct/2009:11:07:49 +0200] [Job 24] envp[24]="FINAL_CONTENT_TYPE=printer/DESKJET-840C"',
               'I [21/Oct/2009:11:07:49 +0200] [Job 24] Started filter /usr/lib/cups/filter/pstopdf (PID 4075)',
               'I [21/Oct/2009:11:07:49 +0200] [Job 24] Started filter /usr/lib/cups/filter/pdftopdf (PID 4076)',
               'I [21/Oct/2009:11:07:49 +0200] [Job 24] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4077)',
               'E [21/Oct/2009:11:07:49 +0200] Unable to execute /usr/lib/cups/backend/hp: No such file or directory',
               'E [21/Oct/2009:11:07:49 +0200] [Job 24] Unable to start backend "hp" - Success.',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'I [21/Oct/2009:11:07:49 +0200] Saving subscriptions.conf...',
               'D [21/Oct/2009:11:07:49 +0200] PID 4068 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.',
               'D [21/Oct/2009:11:07:49 +0200] PID 4074 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.',
               'D [21/Oct/2009:11:07:49 +0200] PID 4077 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.',
               'D [21/Oct/2009:11:07:49 +0200] PID 4072 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [21/Oct/2009:11:07:49 +0200] PID 4066 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [21/Oct/2009:11:07:49 +0200] PID 4076 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'E [21/Oct/2009:11:07:49 +0200] PID 4070 (/usr/lib/cups/filter/pstopdf) stopped with status 1!',
               'E [21/Oct/2009:11:07:49 +0200] PID 4075 (/usr/lib/cups/filter/pstopdf) stopped with status 1!',
               'E [21/Oct/2009:11:07:49 +0200] PID 4065 (/usr/lib/cups/filter/pstopdf) stopped with status 1!',
               'D [21/Oct/2009:11:07:50 +0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [21/Oct/2009:11:07:50 +0200] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [21/Oct/2009:11:07:50 +0200] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [21/Oct/2009:11:07:50 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:07:50 +0200] Get-Notifications /',
               'D [21/Oct/2009:11:07:50 +0200] cupsdIsAuthorized: requesting-user-name="peter"',
               'D [21/Oct/2009:11:07:50 +0200] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [21/Oct/2009:11:07:50 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [21/Oct/2009:11:07:50 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:07:50 +0200] Get-Notifications /',
               'D [21/Oct/2009:11:07:50 +0200] cupsdIsAuthorized: requesting-user-name="peter"',
               'D [21/Oct/2009:11:07:50 +0200] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [21/Oct/2009:11:07:50 +0200] cupsdCloseClient: 12',
               'D [21/Oct/2009:11:07:50 +0200] cupsdCloseClient: 9',
               'D [21/Oct/2009:11:07:50 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Oct/2009:11:07:50 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:07:50 +0200] Get-Notifications /',
               'D [21/Oct/2009:11:07:50 +0200] cupsdIsAuthorized: requesting-user-name="peter"',
               'D [21/Oct/2009:11:07:50 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Oct/2009:11:08:00 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Oct/2009:11:08:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:08:00 +0200] Get-Job-Attributes ipp://localhost/jobs/24',
               'D [21/Oct/2009:11:08:00 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Oct/2009:11:08:00 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [21/Oct/2009:11:08:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [21/Oct/2009:11:08:00 +0200] Cancel-Subscription /',
               'D [21/Oct/2009:11:08:00 +0200] cupsdIsAuthorized: requesting-user-name="peter"',
               'I [21/Oct/2009:11:08:00 +0200] Saving subscriptions.conf...',
               'D [21/Oct/2009:11:08:00 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [21/Oct/2009:11:08:00 +0200] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [21/Oct/2009:11:08:00 +0200] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [21/Oct/2009:11:08:00 +0200] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 10 (Locale issues):
{'job_page_size': u'Letter',
 'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

Any suugestions?
Thx

---

