---
title: "Big printing problem"
date: 2011-03-28
forum: General Help
---

### Post by strideredc on 2011-03-28
hi,

i cant print anything? it was working fine then my hp f4280 packed up so i got a old hp 2050 thats was working fine on windows. ubuntu just wont print and i ran the help thing and that said it couldn't find a problem? when you click print the job goes from processing to complete but without the printer doing anything?!?

there are error log messages but there are about 1000000 of them and if i cut and past them they would fill up the forum!

any ideas??

---

### Post by ubudog on 2011-03-28
How many error messages are there?  You can put it into a code block, and make it scrollable, so that we can see it without it taking up the whole page.

---

### Post by ubudog on 2011-03-28
Ok, after a little Googling, I recommend trying the following.

```
sudo apt-get install hplip
```

If that doesn't work, then try this:
```
sudo apt-get install hplip-cups
```

No guarantees, but it may work.

---

### Post by garvinrick4 on 2011-03-28
When you added the printer to Linux did it give you the drivers for your model of HP

---

### Post by strideredc on 2011-03-28
hi, tried the above and its still the same, it does from processing to done with nothing being printed? it also changes my keyboard from UK to USA?!?!?

---

### Post by strideredc on 2011-03-28
> **garvinrick4 said:**
> When you added the printer to Linux did it give you the drivers for your model of HP

yes linux did install it and its showing the correct printer (hp 2050)

---

### Post by strideredc on 2011-03-30
has anyone else got any ideas as i dont want to have to re install as its a real pain in the ...

---

### Post by strideredc on 2011-03-30
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest HP-Deskjet-2050-J510-series (default)>,
 'cups_instance': None,
 'cups_queue': 'HP-Deskjet-2050-J510-series',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://HP/Deskjet%202050%20J510%20series?serial=CN05L13MDV05D1',
                       'printer-info': u'HP Deskjet 2050 J510 series',
                       'printer-is-shared': True,
                       'printer-location': u'matt-laptop',
                       'printer-make-and-model': u'HP DeskJet 2000 - CUPS+Gutenprint v5.2.5 Simplified',
                       'printer-state': 3,
                       'printer-state-message': u'Finished page 1...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP-Deskjet-2050-J510-series'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'usb://HP/Deskjet%202050%20J510%20series?serial=CN05L13MDV05D1',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raster',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'na_legal_8.5x14in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'adobe_CD5Inch_116.064x116.064mm',
                                                     u'adobe_CD3Inch_64.9111x64.9111mm',
                                                     u'adobe_CDCustom_119.944x119.944mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'iso_a4_210x297mm',
                                                     u'custom_min_0.352778x0.352778mm',
                                                     u'custom_max_8.5x14in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': u'none',
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'HP Deskjet 2050 J510 series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'matt-laptop',
                                 'printer-make-and-model': u'HP DeskJet 2000 - CUPS+Gutenprint v5.2.5 Simplified',
                                 'printer-more-info': u'http://localhost:631/printers/HP-Deskjet-2050-J510-series',
                                 'printer-name': u'HP-Deskjet-2050-J510-series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1301482878,
                                 'printer-state-message': u'Finished page 1...',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 167948,
                                 'printer-up-time': 1301482925,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/HP-Deskjet-2050-J510-series'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': False,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'C1L0': {u'StpBrightness': u'None',
                                         u'StpColorCorrection': u'None',
                                         u'StpContrast': u'None',
                                         u'StpImageType': u'TextGraphics',
                                         u'StpSaturation': u'None'},
                               u'General': {u'ColorModel': u'RGB',
                                            u'InputSlot': u'Standard',
                                            u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'301x300dpi',
                                            u'StpQuality': u'Standard',
                                            u'StpiShrinkOutput': u'Shrink'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:HP;MDL:Deskjet 2050 J510 series;CMD:PCL,DW-PCL,DESKJET,DYN;CLS:PRINTER;DES:CH355B;CID:HPIJVIPAV1;LEDMDIS:USB#07-01-02,USB#FF-CC-00;SN:CN05L13MDV05D1;S:038000C4840F1021022c1f00032c2880046;J:                    ;Z:0102,050399e9009069,0600,0c0,0e00000000,0f00000000,10000008000008,12000,147,150,16361a399e000316da15180003,17000000000000;',
                      'device-info': u'HP Deskjet 2050 J510 series',
                      'device-location': u'',
                      'device-make-and-model': u'HP Deskjet 2050 J510 series'}}
Page 8 (Printer state reasons):
{'printer-state-message': u'Finished page 1...',
 'printer-state-reasons': [u'none']}
Page 9 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 2205L,
 'error_log_debug_logging_set': True}
Page 10 (Print test page):
{'test_page_job_status': [], 'test_page_successful': False}
Page 11 (Error log fetch):
{'error_log': ['D [30/Mar/2011:12:02:38 +0100] cupsdSetBusyState: Dirty files',
               'D [30/Mar/2011:12:02:38 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [30/Mar/2011:12:02:38 +0100] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Mar/2011:12:02:38 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2011:12:02:38 +0100] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [30/Mar/2011:12:02:38 +0100] Get-Jobs ipp://localhost/printers/',
               'D [30/Mar/2011:12:02:38 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [30/Mar/2011:12:02:38 +0100] cupsdSetBusyState: Dirty files',
               'D [30/Mar/2011:12:02:38 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [30/Mar/2011:12:02:38 +0100] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Mar/2011:12:02:38 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2011:12:02:38 +0100] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [30/Mar/2011:12:02:38 +0100] Get-Jobs ipp://localhost/printers/',
               'D [30/Mar/2011:12:02:38 +0100] [Job 30] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 31] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 32] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 33] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 34] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 35] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 36] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 37] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 38] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 39] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 40] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 41] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 42] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 43] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 44] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 45] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 46] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 47] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 48] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 49] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 50] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 51] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 52] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 53] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 54] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] [Job 55] Loading attributes...',
               'D [30/Mar/2011:12:02:38 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [30/Mar/2011:12:02:38 +0100] cupsdSetBusyState: Dirty files',
               'D [30/Mar/2011:12:02:38 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [30/Mar/2011:12:02:38 +0100] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Mar/2011:12:02:38 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2011:12:02:38 +0100] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1',
               'D [30/Mar/2011:12:02:38 +0100] Create-Printer-Subscription /',
               'D [30/Mar/2011:12:02:38 +0100] cupsdCreateSubscription(con=0x22649410(12), uri="/")',
               'D [30/Mar/2011:12:02:38 +0100] pullmethod="ippget"',
               'D [30/Mar/2011:12:02:38 +0100] notify-lease-duration=86400',
               'D [30/Mar/2011:12:02:38 +0100] notify-time-interval=0',
               'D [30/Mar/2011:12:02:38 +0100] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [30/Mar/2011:12:02:38 +0100] Added subscription 34 for server',
               'D [30/Mar/2011:12:02:38 +0100] cupsdMarkDirty(-----S)',
               'D [30/Mar/2011:12:02:38 +0100] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [30/Mar/2011:12:02:38 +0100] cupsdSetBusyState: Dirty files',
               'D [30/Mar/2011:12:02:40 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [30/Mar/2011:12:02:40 +0100] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Mar/2011:12:02:40 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2011:12:02:40 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [30/Mar/2011:12:02:40 +0100] Get-Notifications /',
               'D [30/Mar/2011:12:02:40 +0100] cupsdIsAuthorized: requesting-user-name="matt"',
               'D [30/Mar/2011:12:02:40 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [30/Mar/2011:12:02:40 +0100] cupsdSetBusyState: Dirty files',
               'D [30/Mar/2011:12:02:49 +0100] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [30/Mar/2011:12:02:49 +0100] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Mar/2011:12:02:49 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2011:12:02:49 +0100] cupsdReadClient: 12 1.1 Cancel-Subscription 1',
               'D [30/Mar/2011:12:02:49 +0100] Cancel-Subscription /',
               'D [30/Mar/2011:12:02:49 +0100] cupsdIsAuthorized: requesting-user-name="matt"',
               'D [30/Mar/2011:12:02:49 +0100] cupsdMarkDirty(-----S)',
               'D [30/Mar/2011:12:02:49 +0100] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [30/Mar/2011:12:02:49 +0100] cupsdSetBusyState: Dirty files',
               'D [30/Mar/2011:12:02:49 +0100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [30/Mar/2011:12:02:49 +0100] cupsdReadClient: 14 GET /admin/log/error_log HTTP/1.1',
               'D [30/Mar/2011:12:02:49 +0100] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Mar/2011:12:02:49 +0100] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 12 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by Duncan Williams on 2011-03-30
I'm no expert here but I sorta had the same problem with my canon-mp270 printer.
I deleted the existing printer driver in admin.
Downloaded a deb package for mp270 from Canon Site.
Installed the mp270 package (as well as IJprinter package that was with it)
And it works fine now.

---

### Post by strideredc on 2011-03-30
> **Duncan Williams said:**
> I'm no expert here but I sorta had the same problem with my canon-mp270 printer.
I deleted the existing printer driver in admin.
Downloaded a deb package for mp270 from Canon Site.
Installed the mp270 package (as well as IJprinter package that was with it)
And it works fine now.

Duncan i did what you said and ended up having to do the complicated hp install as the basic doesn't tell you what to put in the command line in the terminal?!?

i dont know exactly what happened but it worked:D buy the way, lovely JRT you have there:D

---

