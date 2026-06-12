---
title: "printer stop working."
date: 2010-02-24
forum: General Help
---

### Post by rizos on 2010-02-24
my lexmark z605 suddenly stop working on ubuntu karmic.


i was able to print normally  till today i run the printer troubleshoot and after asking me some questions, there was no solution but it gave me a troubleshoot log file.

i don't understand what can be wrong, perhaps some of you people can tell me what is the problem...

so here it is...


Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest Lexmark--Z600-Series (default)>,
 'cups_instance': None,
 'cups_queue': 'Lexmark--Z600-Series',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/Z600%20Series',
                       'printer-info': u'Lexmark  Z600 Series',
                       'printer-is-shared': True,
                       'printer-location': u'rizos-desktop',
                       'printer-make-and-model': u'Lexmark Z600 v1.0-1',
                       'printer-state': 3,
                       'printer-state-message': u'Processing page 2...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Lexmark--Z600-Series'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.1',
                                 'device-uri': u'usb://Lexmark/Z600%20Series',
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
                                                     u'iso_a4_210x297mm',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'na_legal_8.5x14in',
                                                     u'jis_b5_182x257mm',
                                                     u'na_executive_7.25x10.5in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-4x6_4x6in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_personal_3.625x6.5in',
                                                     u'na_number-9_3.875x8.875in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_a2_4.375x5.75in',
                                                     u'jpn_chou3_120x235mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'adobe_Chokei40_89.9583x240.947mm',
                                                     u'adobe_Kakugata3_8.5x10.9028in',
                                                     u'adobe_Kakugata4_7.75x10.5139in',
                                                     u'adobe_Kakugata5_190.147x239.889mm',
                                                     u'iso_c5_162x229mm',
                                                     u'adobe_L_3.5x5in',
                                                     u'na_5x7_5x7in',
                                                     u'custom_min_2x4in',
                                                     u'custom_max_8.58333x13in'],
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
                                 'notify-schemes-supported': [u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                       
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 15,
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
                                 'printer-info': u'Lexmark  Z600 Series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'rizos-desktop',
                                 'printer-make-and-model': u'Lexmark Z600 v1.0-1',
                                 'printer-more-info': u'http://localhost:631/printers/Lexmark--Z600-Series',
                                 'printer-name': u'Lexmark--Z600-Series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1267032079,
                                 'printer-state-message': u'Processing page 2...',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 167948,
                                 'printer-up-time': 1267032976,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Lexmark--Z600-Series'],
                                 'queued-job-count': 2,
                                 'server-is-sharing-printers': False,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'},
                               u'Others': {u'ColorModel': u'Color',
                                           u'Inkset': u'CMYK',
                                           u'PrintQuality': u'Normal'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Lexmark ;CMD:CPDNPA001;MODEL:Z600 Series;CLASS:Printer;DES:Lexmark Z600 Series;COMMENT:021127-1;',
                      'device-info': u'Lexmark Z600 Series',
                      'device-make-and-model': u'Lexmark Z600 Series'}}

               'D [24/Feb/2010:11:57:45 -0600] cupsdCloseClient: 15',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
               'D [24/Feb/2010:11:57:50 -0600] Get-Job-Attributes ipp://localhost/jobs/41',
               'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/41) from localhost',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
               'D [24/Feb/2010:11:57:50 -0600] Get-Job-Attributes ipp://localhost/jobs/43',
               'D [24/Feb/2010:11:57:50 -0600] [Job 43] Loading attributes...',
               'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/43) from localhost',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Cancel-Subscription 1',
               'D [24/Feb/2010:11:57:50 -0600] Cancel-Subscription /',
               'D [24/Feb/2010:11:57:50 -0600] cupsdIsAuthorized: requesting-user-name="rizos"',
               'D [24/Feb/2010:11:57:50 -0600] cupsdMarkDirty(-----S)',
               'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
               'I [24/Feb/2010:11:58:12 -0600] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [24/Feb/2010:11:58:12 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2010:11:58:12 -0600] cupsdSetBusyState: Not busy',
               'D [24/Feb/2010:11:58:12 -0600] Report: clients=5',
               'D [24/Feb/2010:11:58:12 -0600] Report: jobs=38',
               'D [24/Feb/2010:11:58:12 -0600] Report: jobs-active=3',
               'D [24/Feb/2010:11:58:12 -0600] Report: printers=1',
               'D [24/Feb/2010:11:58:12 -0600] Report: printers-implicit=0',
               'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-string-count=1904',
               'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-alloc-bytes=8824',
               'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-total-bytes=43088',
               'D [24/Feb/2010:11:58:16 -0600] cupsdAcceptClient: 15 from localhost (Domain)',
               'D [24/Feb/2010:11:58:16 -0600] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1',
               'D [24/Feb/2010:11:58:16 -0600] cupsdSetBusyState: Active clients',
               'D [24/Feb/2010:11:58:16 -0600] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 12 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}



thanx in advance. 


cheers.

---

### Post by drdanielfc on 2010-02-24
> **rizos said:**
> my lexmark z605 suddenly stop working on ubuntu karmic.


i was able to print normally  till today i run the printer troubleshoot and after asking me some questions, there was no solution but it gave me a troubleshoot log file.

i don't understand what can be wrong, perhaps some of you people can tell me what is the problem...

so here it is...


Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest Lexmark--Z600-Series (default)>,
 'cups_instance': None,
 'cups_queue': 'Lexmark--Z600-Series',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Lexmark/Z600%20Series',
                       'printer-info': u'Lexmark  Z600 Series',
                       'printer-is-shared': True,
                       'printer-location': u'rizos-desktop',
                       'printer-make-and-model': u'Lexmark Z600 v1.0-1',
                       'printer-state': 3,
                       'printer-state-message': u'Processing page 2...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Lexmark--Z600-Series'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.1',
                                 'device-uri': u'usb://Lexmark/Z600%20Series',
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
                                                     u'iso_a4_210x297mm',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'na_legal_8.5x14in',
                                                     u'jis_b5_182x257mm',
                                                     u'na_executive_7.25x10.5in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-4x6_4x6in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_personal_3.625x6.5in',
                                                     u'na_number-9_3.875x8.875in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_a2_4.375x5.75in',
                                                     u'jpn_chou3_120x235mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'adobe_Chokei40_89.9583x240.947mm',
                                                     u'adobe_Kakugata3_8.5x10.9028in',
                                                     u'adobe_Kakugata4_7.75x10.5139in',
                                                     u'adobe_Kakugata5_190.147x239.889mm',
                                                     u'iso_c5_162x229mm',
                                                     u'adobe_L_3.5x5in',
                                                     u'na_5x7_5x7in',
                                                     u'custom_min_2x4in',
                                                     u'custom_max_8.58333x13in'],
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
                                 'notify-schemes-supported': [u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                       
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 15,
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
                                 'printer-info': u'Lexmark  Z600 Series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'rizos-desktop',
                                 'printer-make-and-model': u'Lexmark Z600 v1.0-1',
                                 'printer-more-info': u'http://localhost:631/printers/Lexmark--Z600-Series',
                                 'printer-name': u'Lexmark--Z600-Series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1267032079,
                                 'printer-state-message': u'Processing page 2...',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 167948,
                                 'printer-up-time': 1267032976,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Lexmark--Z600-Series'],
                                 'queued-job-count': 2,
                                 'server-is-sharing-printers': False,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'},
                               u'Others': {u'ColorModel': u'Color',
                                           u'Inkset': u'CMYK',
                                           u'PrintQuality': u'Normal'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Lexmark ;CMD:CPDNPA001;MODEL:Z600 Series;CLASS:Printer;DES:Lexmark Z600 Series;COMMENT:021127-1;',
                      'device-info': u'Lexmark Z600 Series',
                      'device-make-and-model': u'Lexmark Z600 Series'}}

               'D [24/Feb/2010:11:57:45 -0600] cupsdCloseClient: 15',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
               'D [24/Feb/2010:11:57:50 -0600] Get-Job-Attributes ipp://localhost/jobs/41',
               'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/41) from localhost',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
               'D [24/Feb/2010:11:57:50 -0600] Get-Job-Attributes ipp://localhost/jobs/43',
               'D [24/Feb/2010:11:57:50 -0600] [Job 43] Loading attributes...',
               'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/43) from localhost',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Cancel-Subscription 1',
               'D [24/Feb/2010:11:57:50 -0600] Cancel-Subscription /',
               'D [24/Feb/2010:11:57:50 -0600] cupsdIsAuthorized: requesting-user-name="rizos"',
               'D [24/Feb/2010:11:57:50 -0600] cupsdMarkDirty(-----S)',
               'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
               'I [24/Feb/2010:11:58:12 -0600] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [24/Feb/2010:11:58:12 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2010:11:58:12 -0600] cupsdSetBusyState: Not busy',
               'D [24/Feb/2010:11:58:12 -0600] Report: clients=5',
               'D [24/Feb/2010:11:58:12 -0600] Report: jobs=38',
               'D [24/Feb/2010:11:58:12 -0600] Report: jobs-active=3',
               'D [24/Feb/2010:11:58:12 -0600] Report: printers=1',
               'D [24/Feb/2010:11:58:12 -0600] Report: printers-implicit=0',
               'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-string-count=1904',
               'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-alloc-bytes=8824',
               'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-total-bytes=43088',
               'D [24/Feb/2010:11:58:16 -0600] cupsdAcceptClient: 15 from localhost (Domain)',
               'D [24/Feb/2010:11:58:16 -0600] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1',
               'D [24/Feb/2010:11:58:16 -0600] cupsdSetBusyState: Active clients',
               'D [24/Feb/2010:11:58:16 -0600] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 12 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}



thanx in advance. 


cheers.

I had a similar problem once, ill see if I can find you my solution but first try this:
```
sudo /etc/init.d/cups restart
```

edit: also, when posting large amounts of info like command outputs make sure you use CODE tags

---

### Post by rizos on 2010-02-24
sorry im a new...

what is CODE tags.


i try your solution and nothing.

---

### Post by drdanielfc on 2010-02-24
> **rizos said:**
> sorry im a new...

what is CODE tags.


i try your solution and nothing.

when you post an output of something click the # button on your toolbar so it wraps it in [_code] tags. then it comes up like this:
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest Lexmark--Z600-Series (default)>,
'cups_instance': None,
'cups_queue': 'Lexmark--Z600-Series',
'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
'cups_printer_dict': {'device-uri': u'usb://Lexmark/Z600%20Series',
'printer-info': u'Lexmark Z600 Series',
'printer-is-shared': True,
'printer-location': u'rizos-desktop',
'printer-make-and-model': u'Lexmark Z600 v1.0-1',
'printer-state': 3,
'printer-state-message': u'Processing page 2...',
'printer-state-reasons': [u'none'],
'printer-type': 167948,
'printer-uri-supported': u'ipp://localhost:631/printers/Lexmark--Z600-Series'},
'cups_printer_remote': False,
'is_cups_class': False,
'local_cups_queue_attributes': {'auth-info-required': u'none',
'charset-configured': u'utf-8',
'charset-supported': [u'us-ascii', u'utf-8'],
'color-supported': True,
'compression-supported': [u'none', u'gzip'],
'copies-default': 1,
'copies-supported': (1, 9999),
'cups-version': u'1.4.1',
'device-uri': u'usb://Lexmark/Z600%20Series',
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
u'iso_a4_210x297mm',
u'na_invoice_5.5x8.5in',
u'na_legal_8.5x14in',
u'jis_b5_182x257mm',
u'na_executive_7.25x10.5in',
u'iso_a5_148x210mm',
u'iso_a6_105x148mm',
u'na_index-3x5_3x5in',
u'na_index-4x6_4x6in',
u'jpn_hagaki_100x148mm',
u'na_personal_3.625x6.5in',
u'na_number-9_3.875x8.875in',
u'na_number-10_4.125x9.5in',
u'iso_dl_110x220mm',
u'iso_c5_162x229mm',
u'iso_c6_114x162mm',
u'iso_b5_176x250mm',
u'na_monarch_3.875x7.5in',
u'na_a2_4.375x5.75in',
u'jpn_chou3_120x235mm',
u'jpn_chou4_90x205mm',
u'adobe_Chokei40_89.9583x240.947mm',
u'adobe_Kakugata3_8.5x10.9028in',
u'adobe_Kakugata4_7.75x10.5139in',
u'adobe_Kakugata5_190.147x239.889mm',
u'iso_c5_162x229mm',
u'adobe_L_3.5x5in',
u'na_5x7_5x7in',
u'custom_min_2x4in',
u'custom_max_8.58333x13in'],
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
'notify-schemes-supported': [u'mailto',
u'rss'],
'number-up-default': 1,
'number-up-supported': [1, 2, 4, 6, 9, 16],
'operations-supported': [2,
4,

16423],
'orientation-requested-default': None,
'orientation-requested-supported': [3,
4,
5,
6],
'page-ranges-supported': True,
'pages-per-minute': 15,
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
'printer-info': u'Lexmark Z600 Series',
'printer-is-accepting-jobs': True,
'printer-is-shared': True,
'printer-location': u'rizos-desktop',
'printer-make-and-model': u'Lexmark Z600 v1.0-1',
'printer-more-info': u'http://localhost:631/printers/Lexmark--Z600-Series',
'printer-name': u'Lexmark--Z600-Series',
'printer-op-policy': u'default',
'printer-op-policy-supported': [u'authenticated',
u'default'],
'printer-settable-attributes-supported': [u'printer-info',
u'printer-location'],
'printer-state': 3,
'printer-state-change-time': 1267032079,
'printer-state-message': u'Processing page 2...',
'printer-state-reasons': [u'none'],
'printer-type': 167948,
'printer-up-time': 1267032976,
'printer-uri-supported': [u'ipp://localhost:631/printers/Lexmark--Z600-Series'],
'queued-job-count': 2,
'server-is-sharing-printers': False,
'uri-authentication-supported': [u'requesting-user-name'],
'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'MediaType': u'Plain',
u'PageRegion': u'Letter',
u'PageSize': u'Letter'},
u'Others': {u'ColorModel': u'Color',
u'Inkset': u'CMYK',
u'PrintQuality': u'Normal'}},
'cups_printer_ppd_valid': True,
'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
'device-id': u'MFG:Lexmark ;CMD:CPDNPA001;MODEL:Z600 Series;CLASSrinter;DES:Lexmark Z600 Series;COMMENT:021127-1;',
'device-info': u'Lexmark Z600 Series',
'device-make-and-model': u'Lexmark Z600 Series'}}

'D [24/Feb/2010:11:57:45 -0600] cupsdCloseClient: 15',
'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
'D [24/Feb/2010:11:57:50 -0600] Get-Job-Attributes ipp://localhost/jobs/41',
'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/41) from localhost',
'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
'D [24/Feb/2010:11:57:50 -0600] Get-Job-Attributes ipp://localhost/jobs/43',
'D [24/Feb/2010:11:57:50 -0600] [Job 43] Loading attributes...',
'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/43) from localhost',
'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Active clients and dirty files',
'D [24/Feb/2010:11:57:50 -0600] cupsdAuthorize: No authentication data provided.',
'D [24/Feb/2010:11:57:50 -0600] cupsdReadClient: 11 1.1 Cancel-Subscription 1',
'D [24/Feb/2010:11:57:50 -0600] Cancel-Subscription /',
'D [24/Feb/2010:11:57:50 -0600] cupsdIsAuthorized: requesting-user-name="rizos"',
'D [24/Feb/2010:11:57:50 -0600] cupsdMarkDirty(-----S)',
'D [24/Feb/2010:11:57:50 -0600] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
'D [24/Feb/2010:11:57:50 -0600] cupsdSetBusyState: Dirty files',
'I [24/Feb/2010:11:58:12 -0600] Saving job cache file "/var/cache/cups/job.cache"...',
'I [24/Feb/2010:11:58:12 -0600] Saving subscriptions.conf...',
'D [24/Feb/2010:11:58:12 -0600] cupsdSetBusyState: Not busy',
'D [24/Feb/2010:11:58:12 -0600] Report: clients=5',
'D [24/Feb/2010:11:58:12 -0600] Report: jobs=38',
'D [24/Feb/2010:11:58:12 -0600] Report: jobs-active=3',
'D [24/Feb/2010:11:58:12 -0600] Report: printers=1',
'D [24/Feb/2010:11:58:12 -0600] Report: printers-implicit=0',
'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-string-count=1904',
'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-alloc-bytes=8824',
'D [24/Feb/2010:11:58:12 -0600] Report: stringpool-total-bytes=43088',
'D [24/Feb/2010:11:58:16 -0600] cupsdAcceptClient: 15 from localhost (Domain)',
'D [24/Feb/2010:11:58:16 -0600] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1',
'D [24/Feb/2010:11:58:16 -0600] cupsdSetBusyState: Active clients',
'D [24/Feb/2010:11:58:16 -0600] cupsdAuthorize: No authentication data provided.'],
'error_log_debug_logging_unset': True}
Page 12 (Locale issues):
{'printer_page_size': u'Letter',
'system_locale_lang': None,
'user_locale_ctype': 'en_US',
'user_locale_messages': 'en_US'}
```

Also, what does the command that I gave you output?

---

### Post by rizos on 2010-02-25
thanx a lot for explaining me...


the output of the command was...


* Restarting Common Unix Printing System: cupsd                         [ OK ]

---

### Post by drdanielfc on 2010-02-25
> **rizos said:**
> thanx a lot for explaining me...


the output of the command was...


* Restarting Common Unix Printing System: cupsd                         [ OK ]

try reinstalling cups-that looks like the problem

---

### Post by rizos on 2010-02-25
thanx drdanielfc for helping me...


i re-install via synaptic cups and still dosent work...



the same log file...


any other idea?...


cheers...

---

### Post by drdanielfc on 2010-02-26
> **rizos said:**
> thanx drdanielfc for helping me...


i re-install via synaptic cups and still dosent work...



the same log file...


any other idea?...


cheers...

does printing work off of a windows computer? because now that i look twice, the log file looks alright...

---

### Post by rizos on 2010-02-26
printer works fine in windows laptop...

i wonder what means cupsdAuthorize: No authentication data provided.


seems like a problem...

---

### Post by drdanielfc on 2010-02-26
> **rizos said:**
> printer works fine in windows laptop...

i wonder what means cupsdAuthorize: No authentication data provided.


seems like a problem...

shouldnt be unless your printer has a password. Can you post a screenshot of your printer config?

---

### Post by rizos on 2010-02-26
oh no my printer dosent have a passwrod...


i re install the driver again from this instructions ([http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150.](http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150.))...and when i try to restart the cups daemon i get this message "bash: /etc/rc2.d/S19cupsys: No such file or directory"

could this be the issue?...

is this what u mean with the printing screenshot?


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148310&stc=1&d=1267211244[/IMG]


thanx again...

---

### Post by rizos on 2010-02-26
i solved the problem... re-strating cups did the trick via this command

 sudo /etc/init.d/cups restart


and now is working...

---

### Post by drdanielfc on 2010-02-26
> **rizos said:**
> i solved the problem... re-strating cups did the trick via this command

 sudo /etc/init.d/cups restart


and now is working...

try restarting your computer first to double check, cups might not restart on its own

---

