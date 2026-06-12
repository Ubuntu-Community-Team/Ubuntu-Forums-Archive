---
title: "I got no clue what is going with my printer"
date: 2010-03-22
forum: General Help
---

### Post by hart02 on 2010-03-22
I can't seem to figure out what is going on that i cannot print. I have always used the hp deskjet 990c driver.Now it will not print. I did the troubleshooting wizard and got this


```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest NetPrinter (default)>,
 'cups_instance': None,
 'cups_queue': 'NetPrinter',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'socket',
 'cups_printer_dict': {'device-uri': u'socket://192.168.1.197:9100',
                       'printer-info': u'Main',
                       'printer-is-shared': True,
                       'printer-location': u'Living Room',
                       'printer-make-and-model': u'HP DeskJet 990C - CUPS+Gutenprint v5.2.4',
                       'printer-state': 3,
                       'printer-state-message': u'Ready to print.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167964,
                       'printer-uri-supported': u'ipp://localhost:631/printers/NetPrinter'},
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
                                 'device-uri': u'socket://192.168.1.197:9100',
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
                                                     u'na_index-3x5_3x5in',
                                                     u'adobe_w252h360_3.5x5in',
                                                     u'na_index-4x6_4x6in',
                                                     u'adobe_w324h495_4.5x6.875in',
                                                     u'iso_a6_105x148mm',
                                                     u'na_5x7_5x7in',
                                                     u'na_index-5x8_5x8in',
                                                     u'na_index-4x6-ext_6x8in',
                                                     u'na_govt-letter_8x10in',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'adobe_w576h864_8x12in',
                                                     u'iso_a4_210x297mm',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'iso_a7_74x105mm',
                                                     u'iso_a8_52x74mm',
                                                     u'iso_a9_37x52mm',
                                                     u'iso_a10_26x37mm',
                                                     u'na_fanfold-eur_8.5x12in',
                                                     u'iso_b5_176x250mm',
                                                     u'iso_b6_125x176mm',
                                                     u'iso_b7_88x125mm',
                                                     u'iso_b8_62x88mm',
                                                     u'iso_b9_44x62mm',
                                                     u'iso_b10_31x44mm',
                                                     u'jis_b5_182x257mm',
                                                     u'jis_b6_128x182mm',
                                                     u'jis_b7_91x128mm',
                                                     u'jis_b8_64x91mm',
                                                     u'iso_b9_44x62mm',
                                                     u'iso_b10_31x44mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_b6c4_125x324mm',
                                                     u'iso_c6_114x162mm',
                                                     u'adobe_C6_l_6.375x4.48611in',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_c7c6_81x162mm',
                                                     u'adobe_w229h459_l_6.375x3.18056in',
                                                     u'iso_c7_81x114mm',
                                                     u'adobe_C7_l_113.947x80.7861mm',
                                                     u'iso_c8_57x81mm',
                                                     u'adobe_C8_l_80.7861x56.7972mm',
                                                     u'iso_c9_40x57mm',
                                                     u'adobe_C9_l_56.7972x39.8639mm',
                                                     u'iso_c10_28x40mm',
                                                     u'adobe_C10_l_39.8639x27.8694mm',
                                                     u'na_foolscap_8.5x13in',
                                                     u'adobe_w535h697_188.736x245.886mm',
                                                     u'adobe_w569h731_200.731x257.881mm',
                                                     u'adobe_w348h527_122.767x185.914mm',
                                                     u'adobe_w365h561_128.764x197.908mm',
                                                     u'adobe_w391h612_5.43056x8.5in',
                                                     u'adobe_w442h663_155.928x233.892mm',
                                                     u'adobe_w314h504_4.36111x7in',
                                                     u'adobe_w314h513_4.36111x7.125in',
                                                     u'adobe_cw365h561_128.764x197.908mm',
                                                     u'om_small-photo_100x150mm',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'jpn_oufuku_148x200mm',
                                                     u'jpn_chou3_120x235mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'adobe_w255h581_l_204.964x89.9583mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'na_a2_4.375x5.75in',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'adobe_Monarch_l_7.5x3.875in',
                                                     u'adobe_w288h387_4x5.375in',
                                                     u'adobe_w288h504_4x7in',
                                                     u'adobe_w253h337_89.2528x118.886mm',
                                                     u'adobe_w155h244_54.6806x86.0778mm',
                                                     u'adobe_w283h566_99.8361x199.672mm',
                                                     u'na_foolscap_8.5x13in',
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
                                 'notify-schemes-supported': [u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
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
                                 'printer-info': u'Main',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'Living Room',
                                 'printer-make-and-model': u'HP DeskJet 990C - CUPS+Gutenprint v5.2.4',
                                 'printer-more-info': u'http://localhost:631/printers/NetPrinter',
                                 'printer-name': u'NetPrinter',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1269229967,
                                 'printer-state-message': u'Ready to print.',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 167964,
                                 'printer-up-time': 1269230000,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/NetPrinter'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'two-sided-short-edge',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'C1L0': {u'StpBrightness': u'None',
                                         u'StpColorCorrection': u'None',
                                         u'StpContrast': u'None',
                                         u'StpFineBrightness': u'None',
                                         u'StpFineContrast': u'None',
                                         u'StpFineSaturation': u'None',
                                         u'StpImageType': u'TextGraphics',
                                         u'StpSaturation': u'None'},
                               u'C1L1': {u'StpBlackDensity': u'None',
                                         u'StpCyanDensity': u'None',
                                         u'StpDensity': u'None',
                                         u'StpDitherAlgorithm': u'None',
                                         u'StpFineBlackDensity': u'None',
                                         u'StpFineCyanDensity': u'None',
                                         u'StpFineDensity': u'None',
                                         u'StpFineMagentaDensity': u'None',
                                         u'StpFineYellowDensity': u'None',
                                         u'StpMagentaDensity': u'None',
                                         u'StpYellowDensity': u'None'},
                               u'C1L2': {u'StpBlackGamma': u'None',
                                         u'StpCyanBalance': u'None',
                                         u'StpCyanGamma': u'None',
                                         u'StpFineBlackGamma': u'None',
                                         u'StpFineCyanBalance': u'None',
                                         u'StpFineCyanGamma': u'None',
                                         u'StpFineGamma': u'None',
                                         u'StpFineMagentaBalance': u'None',
                                         u'StpFineMagentaGamma': u'None',
                                         u'StpFineYellowBalance': u'None',
                                         u'StpFineYellowGamma': u'None',
                                         u'StpGamma': u'None',
                                         u'StpMagentaBalance': u'None',
                                         u'StpMagentaGamma': u'None',
                                         u'StpYellowBalance': u'None',
                                         u'StpYellowGamma': u'None'},
                               u'C1L4': {u'StpLinearContrast': u'False'},
                               u'C1L5': {u'StpBlackTrans': u'None',
                                         u'StpFineBlackTrans': u'None',
                                         u'StpFineGCRLower': u'None',
                                         u'StpFineGCRUpper': u'None',
                                         u'StpFineInkLimit': u'None',
                                         u'StpGCRLower': u'None',
                                         u'StpGCRUpper': u'None',
                                         u'StpInkLimit': u'None'},
                               u'General': {u'ColorModel': u'RGB',
                                            u'Duplex': u'DuplexTumble',
                                            u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'301x300dpi',
                                            u'StpColorPrecision': u'Normal',
                                            u'StpQuality': u'Standard',
                                            u'StpiShrinkOutput': u'Shrink'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Printer state reasons):
{'printer-state-message': u'Ready to print.',
 'printer-state-reasons': [u'none']}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '1',
                          '_remote_any': '1',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 706693L}
Page 8 (Print test page):
{'test_page_attempted': '21/Mar/2010:23:53:27 +0000',
 'test_page_job_id': [4],
 'test_page_job_status': [(True,
                           4,
                           'NetPrinter',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 4,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/4',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'brian',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/pdftopdf failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1269230016,
                            'job-printer-uri': u'ipp://bmansdesktop:631/printers/NetPrinter',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/4',
                            'job-uuid': u'urn:uuid:9be2dbd8-9fad-3274-4670-d0f31bdf5bb2',
                            'printer-uri': u'ipp://localhost/printers/NetPrinter',
                            'time-at-completed': None,
                            'time-at-creation': 1269230007,
                            'time-at-processing': 1269230007})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [21/Mar/2010:23:53:25 -0400] cupsdSetBusyState: Not busy',
               'D [21/Mar/2010:23:53:25 -0400] cupsdReadClient: 191 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:25 -0400] cupsdSetBusyState: Active clients',
               'D [21/Mar/2010:23:53:25 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:25 -0400] cupsdReadClient: 191 1.1 Get-Jobs 1',
               'D [21/Mar/2010:23:53:25 -0400] Get-Jobs ipp://localhost/printers/',
               'D [21/Mar/2010:23:53:25 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [21/Mar/2010:23:53:25 -0400] cupsdSetBusyState: Not busy',
               'D [21/Mar/2010:23:53:25 -0400] cupsdReadClient: 191 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:25 -0400] cupsdSetBusyState: Active clients',
               'D [21/Mar/2010:23:53:25 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:25 -0400] cupsdReadClient: 191 1.1 Get-Jobs 1',
               'D [21/Mar/2010:23:53:25 -0400] Get-Jobs ipp://localhost/printers/',
               'D [21/Mar/2010:23:53:25 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [21/Mar/2010:23:53:25 -0400] cupsdSetBusyState: Not busy',
               'D [21/Mar/2010:23:53:25 -0400] cupsdReadClient: 191 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:25 -0400] cupsdSetBusyState: Active clients',
               'D [21/Mar/2010:23:53:25 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:25 -0400] cupsdReadClient: 191 1.1 Create-Printer-Subscription 1',
               'D [21/Mar/2010:23:53:25 -0400] Create-Printer-Subscription /',
               'D [21/Mar/2010:23:53:25 -0400] cupsdCreateSubscription(con=0x2294bb28(191), uri="/")',
               'D [21/Mar/2010:23:53:25 -0400] pullmethod="ippget"',
               'D [21/Mar/2010:23:53:25 -0400] notify-lease-duration=86400',
               'D [21/Mar/2010:23:53:25 -0400] notify-time-interval=0',
               'D [21/Mar/2010:23:53:25 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [21/Mar/2010:23:53:25 -0400] Added subscription 6 for server',
               'D [21/Mar/2010:23:53:25 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:25 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:25 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [21/Mar/2010:23:53:25 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:26 -0400] cupsdReadClient: 191 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:26 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:26 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:26 -0400] cupsdReadClient: 191 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:26 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:26 -0400] cupsdIsAuthorized: username="brian"',
               'D [21/Mar/2010:23:53:26 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:26 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:27 -0400] cupsdAcceptClient: 192 from localhost (Domain)',
               'D [21/Mar/2010:23:53:27 -0400] cupsdReadClient: 183 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:27 -0400] cupsdCloseClient: 183',
               'D [21/Mar/2010:23:53:27 -0400] cupsdReadClient: 185 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:27 -0400] cupsdCloseClient: 185',
               'D [21/Mar/2010:23:53:27 -0400] cupsdReadClient: 184 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:27 -0400] cupsdCloseClient: 184',
               'D [21/Mar/2010:23:53:27 -0400] cupsdReadClient: 192 POST /printers/NetPrinter HTTP/1.1',
               'D [21/Mar/2010:23:53:27 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:27 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:27 -0400] cupsdReadClient: 192 1.1 Print-Job 1',
               'D [21/Mar/2010:23:53:27 -0400] Print-Job ipp://localhost/printers/NetPrinter',
               'D [21/Mar/2010:23:53:27 -0400] [Job ???] Auto-typing file...',
               'I [21/Mar/2010:23:53:27 -0400] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(----J-)',
               'D [21/Mar/2010:23:53:27 -0400] add_job: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:27 -0400] Adding default job-sheets values "none,none"...',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Adding start banner page "none".',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(----J-)',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Adding end banner page "none".',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] File of type application/vnd.cups-banner queued by "brian".',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] hold_until=0',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Queued on "NetPrinter" by "brian".',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(----J-)',
               'D [21/Mar/2010:23:53:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] job-sheets=none,none',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] argv[0]="NetPrinter"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] argv[1]="4"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] argv[2]="brian"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] argv[3]="Test Page"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] argv[4]="1"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] argv[5]="job-uuid=urn:uuid:9be2dbd8-9fad-3274-4670-d0f31bdf5bb2 job-originating-host-name=localhost"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] argv[6]="/var/spool/cups/d00004-001"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[10]="SERVER_ADMIN=root@bmansdesktop"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[11]="SOFTWARE=CUPS/1.4.1"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[13]="TZ=America/New_York"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[14]="USER=root"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[17]="IPP_PORT=631"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[18]="CHARSET=utf-8"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[19]="LANG=en_US.UTF-8"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[20]="PPD=/etc/cups/ppd/NetPrinter.ppd"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[21]="RIP_MAX_CACHE=2064853k"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[23]="DEVICE_URI=socket://192.168.1.197:9100"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[24]="PRINTER_INFO=Main"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[25]="PRINTER_LOCATION=Living Room"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[26]="PRINTER=NetPrinter"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[27]="CUPS_FILETYPE=document"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[28]="FINAL_CONTENT_TYPE=printer/NetPrinter"',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Started filter /usr/lib/cups/filter/bannertops (PID 30078)',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Started filter /usr/lib/cups/filter/pstopdf (PID 30079)',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Started filter /usr/lib/cups/filter/pdftopdf (PID 30080)',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Started filter /usr/lib/cups/filter/pdftoraster (PID 30081)',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Started filter /usr/lib/cups/filter/rastertogutenprint.5.2 (PID 30082)',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Started backend /usr/lib/cups/backend/socket (PID 30083)',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/NetPrinter) from localhost',
               'D [21/Mar/2010:23:53:27 -0400] PID 30080 (/usr/lib/cups/filter/pdftopdf) stopped with status 127!',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] load_banner(filename="/var/spool/cups/d00004-001")',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] NetPrinter: symbol lookup error: NetPrinter: undefined symbol: _ZN13GfxColorSpace5parseEP6Object',
               'D [21/Mar/2010:23:53:27 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] STATE: +connecting-to-device',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Looking up "192.168.1.197"...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Connecting to 192.168.1.197:9100',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Connecting to printer...',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] STATE: -connecting-to-device',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Connected to printer...',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Connected to 192.168.1.197:9100 (IPv4)...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Page = 612x792; 18,33 to 594,789',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Courier" - No such file or directory',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Courier-Bold" - No such file or directory',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Courier-Bold-Italic" - No such file or directory',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Courier-Italic" - No such file or directory',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Symbol" - No such file or directory',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] pstopdf 5 args: 4 brian Test Page 1 job-uuid=urn:uuid:9be2dbd8-9fad-3274-4670-d0f31bdf5bb2 job-originating-host-name=localhost',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] PPD: /etc/cups/ppd/NetPrinter.ppd',
               'D [21/Mar/2010:23:53:27 -0400] PID 30078 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -sMediaType=Plain -dDuplex -r300x300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dTumble -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsRowFeed=3 -scupsPageSizeName=Letter -c -f -_',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[10]="SERVER_ADMIN=root@bmansdesktop"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[11]="SOFTWARE=CUPS/1.4.1"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[12]="TZ=America/New_York"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[13]="USER=root"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[16]="IPP_PORT=631"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[17]="CHARSET=utf-8"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[18]="LANG=en_US.UTF-8"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[19]="PPD=/etc/cups/ppd/NetPrinter.ppd"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[20]="RIP_MAX_CACHE=2064853k"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[22]="DEVICE_URI=socket://192.168.1.197:9100"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[23]="PRINTER_INFO=Main"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[24]="PRINTER_LOCATION=Living Room"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[25]="PRINTER=NetPrinter"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[26]="CUPS_FILETYPE=document"',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] envp[27]="FINAL_CONTENT_TYPE=printer/NetPrinter"',
               'D [21/Mar/2010:23:53:27 -0400] PID 30081 (/usr/lib/cups/filter/pdftoraster) exited with no errors.',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] prtGeneralCurrentLocalization type is 5, expected 2!',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=6, addr=0x228ac844, use_bc=1, side_cb=0xf4b590)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Resolution: 301x300',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint 5.2.4 Starting',
               "D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint command line: NetPrinter '4' 'brian' 'Test Page' '1' <args>",
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint using PPD file /etc/cups/ppd/NetPrinter.ppd',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint: CUPS option count is 2 (90 bytes)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint: CUPS option 0 job-originating-host-name = localhost',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint: CUPS option 1 job-uuid = urn:uuid:9be2dbd8-9fad-3274-4670-d0f31bdf5bb2',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint: Driver HP DeskJet 990C',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint: Using fd 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint: Set options:',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting PageSize to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting MediaType to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting InputSlot to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set string Quality to Standard',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set special string Quality to Standard',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting Resolution to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting InkType to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting InkChannels to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting PrintingMode to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting Duplex to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set string ColorCorrection to None',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set special string ColorCorrection to None',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting ChannelBitDepth to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting InputImageType to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting STPIOutputType to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting STPIRawChannels to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting SimpleGamma to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set bool LinearContrast to False (0)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting LUTDumpFile to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CyanCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting MagentaCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting YellowCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting BlackCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting RedCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting GreenCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting BlueCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting WhiteCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting HueMap to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting SatMap to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting LumMap to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting GCRCurve to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh0 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh1 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh2 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh3 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh4 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh5 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh6 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh7 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh8 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh9 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh10 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh11 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh12 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh13 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh14 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh15 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh16 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh17 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh18 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh19 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh20 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh21 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh22 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh23 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh24 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh25 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh26 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh27 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh28 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh29 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh30 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting CurveCh31 to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set string DitherAlgorithm to None',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set special string DitherAlgorithm to None',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set string ImageType to TextGraphics',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Set special string ImageType to TextGraphics',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting JobMode to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint:   Not setting PageNumber to (null)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Gutenprint: End options',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] num_components = 1, depth = 1',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] max_gray = 1, dither_grays = 2',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] max_color = 0, dither_colors = 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Updating PageSize to [612 792]...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting initial media size, [612 792] = 2550x3300 pixels...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting MediaType to "Plain"...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting Duplex to 1...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting Tumble to 1...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting cupsBitsPerColor to 8...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting cupsColorOrder to 0...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting cupsColorSpace to 1...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting cupsRowFeed to 3...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting cupsPageSizeName to "Letter"...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] num_components = 3, depth = 24',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] max_gray = 0, dither_grays = 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] max_color = 255, dither_colors = 256',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting initial media size, [612 792] = 2550x3300 pixels...',
               'I [21/Mar/2010:23:53:27 -0400] [Job 4] Processing page 1...',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] num_components = 3, depth = 24',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] max_gray = 0, dither_grays = 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] max_color = 255, dither_colors = 256',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Page size: Letter',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Setting LeadingEdge to 0...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] num_components = 3, depth = 24',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] cupsColorSpace = 1, cupsColorOrder = 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] cupsBitsPerPixel = 24, cupsBitsPerColor = 8',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] max_gray = 0, dither_grays = 0',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] max_color = 255, dither_colors = 256',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Updating PageSize to [612 792]...',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] size = Letter',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] margins[] = [ 0.250000 0.458333 0.250000 0.041667 ]',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Width: 612, height: 792, absolute margins: 18, 33, 594, 789',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Relative margins: 18, 33, 18, 3',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] PostScript to be injected:',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Gutenprint: About to start printing loop.',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Gutenprint: Printed total 0 bytes',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Gutenprint: Used 0.040 seconds user, 0.010 seconds system, 0.178 seconds elapsed',
               'D [21/Mar/2010:23:53:28 -0400] PID 30082 (/usr/lib/cups/filter/rastertogutenprint.5.2) exited with no errors.',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] GPL Ghostscript 8.70: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAcceptClient: 184 from localhost:631 (IPv6)',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 184 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 184 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:28 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Printer-Attributes ipp://localhost/printers/Photosmart_C6200',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Photosmart_C6200) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAcceptClient: 185 from localhost:631 (IPv6)',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAcceptClient: 193 from localhost (Domain)',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 185 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 193 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 185 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:28 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 193 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:28 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Printer-Attributes ipp://localhost/printers/Photosmart_C6200',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Photosmart_C6200) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 185 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:28 -0400] cupsdCloseClient: 185',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAcceptClient: 185 from localhost:631 (IPv6)',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 193 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:28 -0400] cupsdCloseClient: 193',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAcceptClient: 193 from localhost (Domain)',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 185 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 193 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Printer-Attributes ipp://localhost/printers/Photosmart_C6200',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Photosmart_C6200) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 185 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:28 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 193 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:28 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 185 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:28 -0400] cupsdCloseClient: 185',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 193 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Printer-Attributes ipp://localhost/printers/Photosmart_C6200',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Photosmart_C6200) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 193 1.1 Get-Job-Attributes 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Printer-Attributes ipp://localhost/printers/Photosmart_C6200',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Photosmart_C6200) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 193 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:28 -0400] cupsdCloseClient: 193',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 191 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 184 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:28 -0400] cupsdCloseClient: 184',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 191 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:28 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:28 -0400] cupsdIsAuthorized: username="brian"',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:28 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:28 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:28 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:28 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Error: /ioerror in --showpage--',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Operand stack:',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] 1   true',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Execution stack:',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1862   1   3   %oparray_pop   1861   1   3   %oparray_pop   1845   1   3   %oparray_pop   1739   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   1745   0   3   %oparray_pop   --nostringval--   --nostringval--',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Dictionary stack:',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] --dict:1161/1684(ro)(G)--   --dict:0/20(G)--   --dict:128/200(L)--',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Current allocation mode is local',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] Last OS error: 32',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] GPL Ghostscript 8.70: Unrecoverable error, exit code 1',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] GPL Ghostscript 8.70: ERROR -12 closing pdfwrite device. See gs/src/ierrors.h for code explanation.',
               'D [21/Mar/2010:23:53:28 -0400] [Job 4] cat: write error: Broken pipe',
               'D [21/Mar/2010:23:53:28 -0400] PID 30079 (/usr/lib/cups/filter/pstopdf) stopped with status 1!',
               'I [21/Mar/2010:23:53:33 -0400] [Job 4] Print file sent, waiting for printer to finish...',
               'D [21/Mar/2010:23:53:33 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdMarkDirty(-----S)',
               'I [21/Mar/2010:23:53:33 -0400] [Job 4] Ready to print.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:33 -0400] PID 30083 (/usr/lib/cups/backend/socket) exited with no errors.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdMarkDirty(-----S)',
               'E [21/Mar/2010:23:53:33 -0400] [Job 4] Job stopped due to filter errors; please consult the error_log file for details.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdMarkDirty(----J-)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] The following messages were recorded from 11:53:27 PM to 11:53:28 PM',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_set_color_info(0x93569ec)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsEncodeLUT[0] = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsEncodeLUT[65535] = 255',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] ppd = (nil)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612.000 792.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] margins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWResolution = [ 300.000 300.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2550, height = 3300',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_open(0x93569ec)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_set_color_info(0x93569ec)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsEncodeLUT[0] = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsEncodeLUT[65535] = 255',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_space_params(0x93569ec, 0xbfd38a8c)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cache_size = 2114409472',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38b18)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2550, height = 3300',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -0.000 3300.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38ac8)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2550, height = 3300',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -0.000 3300.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38b78)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2550, height = 3300',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -0.000 3300.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38b50)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38a88)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2550, height = 3300',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -0.000 3300.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38b38)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2550, height = 3300',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -0.000 3300.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38ae8)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2550, height = 3300',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 0.000 0.000 0.000 0.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -0.000 3300.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38b50)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38b50)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38b50)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38b50)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_put_params(0x93569ec, 0xbfd38b58)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_set_color_info(0x93569ec)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsEncodeLUT[0] = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsEncodeLUT[65535] = 255',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.cupsPageSizeName = Letter',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Reallocating memory, [612 792] = 2400x3150 pixels...',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_space_params(0x93569ec, 0xbfd3885c)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cache_size = 2114409472',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] ppd = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612.000 792.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] margins = [ 0.250 0.458 0.250 0.042 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWResolution = [ 300.000 300.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38a98)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -75.000 3287.500 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38a48)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -75.000 3287.500 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38b18)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -75.000 3287.500 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38ac8)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -75.000 3287.500 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38b50)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38b68)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -75.000 3287.500 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38b50)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38b78)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -75.000 3287.500 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38b50)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38a88)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -75.000 3287.500 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_matrix(0x93569ec, 0xbfd38ae8)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->header.Duplex = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups->page = 1',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD = 0x94915b8',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cupsPPD->flip_duplex = 0',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] width = 2400, height = 3150',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] PageSize = [ 612 792 ], HWResolution = [ 300 300 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] HWMargins = [ 18.000 33.000 18.000 3.000 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] matrix = [ 4.167 0.000 0.000 -4.167 -75.000 3287.500 ]',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38d40)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_get_params(0x93569ec, 0xbfd38d40)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] before gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] after gdev_prn_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] Leaving cups_get_params()',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] cups_close(0x93569ec)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] End of messages',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] printer-state=3(idle)',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] printer-state-message="Ready to print."',
               'D [21/Mar/2010:23:53:33 -0400] [Job 4] printer-state-reasons=none',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAcceptClient: 183 from localhost:631 (IPv6)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAcceptClient: 184 from localhost:631 (IPv6)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 183 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 183 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:33 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAcceptClient: 185 from localhost (Domain)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 185 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 185 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:33 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 184 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Printer-Attributes ipp://localhost/printers/Photosmart_C6200',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Photosmart_C6200) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 184 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:33 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 185 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:33 -0400] cupsdCloseClient: 185',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAcceptClient: 185 from localhost (Domain)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 185 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 185 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:33 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAcceptClient: 193 from localhost (Domain)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 184 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:33 -0400] cupsdCloseClient: 184',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAcceptClient: 184 from localhost:631 (IPv6)',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 193 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 193 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Printer-Attributes ipp://bmansdesktop:631/printers/NetPrinter',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://bmansdesktop:631/printers/NetPrinter) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 193 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 184 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 193 1.1 Get-Job-Attributes 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 184 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:33 -0400] cupsdIsAuthorized: requesting-user-name="brian"',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 185 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:33 -0400] cupsdCloseClient: 185',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 191 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 184 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:33 -0400] cupsdCloseClient: 184',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 191 1.1 Get-Notifications 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Notifications /',
               'D [21/Mar/2010:23:53:33 -0400] cupsdIsAuthorized: username="brian"',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 153 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Printer-Attributes ipp://localhost/printers/Photosmart_C6200',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Photosmart_C6200) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 148 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 Get-Printer-Attributes 1',
               'D [21/Mar/2010:23:53:33 -0400] Get-Printer-Attributes ipp://localhost/printers/Photosmart_C6200',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Photosmart_C6200) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 183 WAITING Closing on EOF',
               'D [21/Mar/2010:23:53:33 -0400] cupsdCloseClient: 183',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Printers 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Printers',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Classes 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Classes',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:33 -0400] cupsdAuthorize: No authentication data provided.',
               'D [21/Mar/2010:23:53:33 -0400] cupsdReadClient: 141 1.1 CUPS-Get-Default 1',
               'D [21/Mar/2010:23:53:33 -0400] CUPS-Get-Default',
               'D [21/Mar/2010:23:53:33 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [21/Mar/2010:23:53:33 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:34 -0400] [Job 4] Unloading...',
               'D [21/Mar/2010:23:53:36 -0400] cupsdReadClient: 191 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:36 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:36 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:36 -0400] cupsdReadClient: 191 1.1 Get-Job-Attributes 1',
               'D [21/Mar/2010:23:53:36 -0400] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [21/Mar/2010:23:53:36 -0400] [Job 4] Loading attributes...',
               'D [21/Mar/2010:23:53:36 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [21/Mar/2010:23:53:36 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:36 -0400] cupsdReadClient: 191 POST / HTTP/1.1',
               'D [21/Mar/2010:23:53:36 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:36 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [21/Mar/2010:23:53:36 -0400] cupsdReadClient: 191 1.1 Cancel-Subscription 1',
               'D [21/Mar/2010:23:53:36 -0400] Cancel-Subscription /',
               'D [21/Mar/2010:23:53:36 -0400] cupsdIsAuthorized: username="brian"',
               'D [21/Mar/2010:23:53:36 -0400] cupsdMarkDirty(-----S)',
               'D [21/Mar/2010:23:53:36 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [21/Mar/2010:23:53:36 -0400] cupsdSetBusyState: Dirty files',
               'D [21/Mar/2010:23:53:36 -0400] cupsdAcceptClient: 183 from localhost (Domain)',
               'D [21/Mar/2010:23:53:36 -0400] cupsdReadClient: 183 GET /admin/log/error_log HTTP/1.1',
               'D [21/Mar/2010:23:53:36 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [21/Mar/2010:23:53:36 -0400] cupsdAuthorize: No authentication data provided.']}
Page 10 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```

I can't tell what the error is or how to fix this. If anyone knows where to look please tell me.

---

### Post by ellgor on 2010-03-22
Hi,

Take a look at this output from that file you supplied :

D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Courier" - No such file or directory',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Courier-Bold" - No such file or directory',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Courier-Bold-Italic" - No such file or directory',
               'D [21/Mar/2010:23:53:27 -0400] [Job 4] Unable to open font file "/usr/share/cups/fonts/Courier-Italic" - No such file or directory',
               'D

from that I would say some fonts are missing on your system, try to locate and install them and see if that helps.

Regards, Ellgor.

---

### Post by hart02 on 2010-03-23
I get this
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest NetPrinter (default)>,
 'cups_instance': None,
 'cups_queue': 'NetPrinter',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'socket',
 'cups_printer_dict': {'device-uri': u'socket://192.168.1.197:9100',
                       'printer-info': u'Main',
                       'printer-is-shared': True,
                       'printer-location': u'Living Room',
                       'printer-make-and-model': u'HP DeskJet 990C - CUPS+Gutenprint v5.2.4',
                       'printer-state': 3,
                       'printer-state-message': u'Ready to print.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167964,
                       'printer-uri-supported': u'ipp://localhost:631/printers/NetPrinter'},
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
                                 'device-uri': u'socket://192.168.1.197:9100',
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
                                                     u'na_index-3x5_3x5in',
                                                     u'adobe_w252h360_3.5x5in',
                                                     u'na_index-4x6_4x6in',
                                                     u'adobe_w324h495_4.5x6.875in',
                                                     u'iso_a6_105x148mm',
                                                     u'na_5x7_5x7in',
                                                     u'na_index-5x8_5x8in',
                                                     u'na_index-4x6-ext_6x8in',
                                                     u'na_govt-letter_8x10in',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'adobe_w576h864_8x12in',
                                                     u'iso_a4_210x297mm',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'iso_a7_74x105mm',
                                                     u'iso_a8_52x74mm',
                                                     u'iso_a9_37x52mm',
                                                     u'iso_a10_26x37mm',
                                                     u'na_fanfold-eur_8.5x12in',
                                                     u'iso_b5_176x250mm',
                                                     u'iso_b6_125x176mm',
                                                     u'iso_b7_88x125mm',
                                                     u'iso_b8_62x88mm',
                                                     u'iso_b9_44x62mm',
                                                     u'iso_b10_31x44mm',
                                                     u'jis_b5_182x257mm',
                                                     u'jis_b6_128x182mm',
                                                     u'jis_b7_91x128mm',
                                                     u'jis_b8_64x91mm',
                                                     u'iso_b9_44x62mm',
                                                     u'iso_b10_31x44mm',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_b6c4_125x324mm',
                                                     u'iso_c6_114x162mm',
                                                     u'adobe_C6_l_6.375x4.48611in',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_c7c6_81x162mm',
                                                     u'adobe_w229h459_l_6.375x3.18056in',
                                                     u'iso_c7_81x114mm',
                                                     u'adobe_C7_l_113.947x80.7861mm',
                                                     u'iso_c8_57x81mm',
                                                     u'adobe_C8_l_80.7861x56.7972mm',
                                                     u'iso_c9_40x57mm',
                                                     u'adobe_C9_l_56.7972x39.8639mm',
                                                     u'iso_c10_28x40mm',
                                                     u'adobe_C10_l_39.8639x27.8694mm',
                                                     u'na_foolscap_8.5x13in',
                                                     u'adobe_w535h697_188.736x245.886mm',
                                                     u'adobe_w569h731_200.731x257.881mm',
                                                     u'adobe_w348h527_122.767x185.914mm',
                                                     u'adobe_w365h561_128.764x197.908mm',
                                                     u'adobe_w391h612_5.43056x8.5in',
                                                     u'adobe_w442h663_155.928x233.892mm',
                                                     u'adobe_w314h504_4.36111x7in',
                                                     u'adobe_w314h513_4.36111x7.125in',
                                                     u'adobe_cw365h561_128.764x197.908mm',
                                                     u'om_small-photo_100x150mm',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'jpn_oufuku_148x200mm',
                                                     u'jpn_chou3_120x235mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'adobe_w255h581_l_204.964x89.9583mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'na_a2_4.375x5.75in',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'adobe_Monarch_l_7.5x3.875in',
                                                     u'adobe_w288h387_4x5.375in',
                                                     u'adobe_w288h504_4x7in',
                                                     u'adobe_w253h337_89.2528x118.886mm',
                                                     u'adobe_w155h244_54.6806x86.0778mm',
                                                     u'adobe_w283h566_99.8361x199.672mm',
                                                     u'na_foolscap_8.5x13in',
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
                                 'notify-schemes-supported': [u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
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
                                 'printer-info': u'Main',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'Living Room',
                                 'printer-make-and-model': u'HP DeskJet 990C - CUPS+Gutenprint v5.2.4',
                                 'printer-more-info': u'http://localhost:631/printers/NetPrinter',
                                 'printer-name': u'NetPrinter',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1269322129,
                                 'printer-state-message': u'Ready to print.',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 167964,
                                 'printer-up-time': 1269322368,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/NetPrinter'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'two-sided-short-edge',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'C1L0': {u'StpBrightness': u'None',
                                         u'StpColorCorrection': u'None',
                                         u'StpContrast': u'None',
                                         u'StpFineBrightness': u'None',
                                         u'StpFineContrast': u'None',
                                         u'StpFineSaturation': u'None',
                                         u'StpImageType': u'TextGraphics',
                                         u'StpSaturation': u'None'},
                               u'C1L1': {u'StpBlackDensity': u'None',
                                         u'StpCyanDensity': u'None',
                                         u'StpDensity': u'None',
                                         u'StpDitherAlgorithm': u'None',
                                         u'StpFineBlackDensity': u'None',
                                         u'StpFineCyanDensity': u'None',
                                         u'StpFineDensity': u'None',
                                         u'StpFineMagentaDensity': u'None',
                                         u'StpFineYellowDensity': u'None',
                                         u'StpMagentaDensity': u'None',
                                         u'StpYellowDensity': u'None'},
                               u'C1L2': {u'StpBlackGamma': u'None',
                                         u'StpCyanBalance': u'None',
                                         u'StpCyanGamma': u'None',
                                         u'StpFineBlackGamma': u'None',
                                         u'StpFineCyanBalance': u'None',
                                         u'StpFineCyanGamma': u'None',
                                         u'StpFineGamma': u'None',
                                         u'StpFineMagentaBalance': u'None',
                                         u'StpFineMagentaGamma': u'None',
                                         u'StpFineYellowBalance': u'None',
                                         u'StpFineYellowGamma': u'None',
                                         u'StpGamma': u'None',
                                         u'StpMagentaBalance': u'None',
                                         u'StpMagentaGamma': u'None',
                                         u'StpYellowBalance': u'None',
                                         u'StpYellowGamma': u'None'},
                               u'C1L4': {u'StpLinearContrast': u'False'},
                               u'C1L5': {u'StpBlackTrans': u'None',
                                         u'StpFineBlackTrans': u'None',
                                         u'StpFineGCRLower': u'None',
                                         u'StpFineGCRUpper': u'None',
                                         u'StpFineInkLimit': u'None',
                                         u'StpGCRLower': u'None',
                                         u'StpGCRUpper': u'None',
                                         u'StpInkLimit': u'None'},
                               u'General': {u'ColorModel': u'RGB',
                                            u'Duplex': u'DuplexTumble',
                                            u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'301x300dpi',
                                            u'StpColorPrecision': u'Normal',
                                            u'StpQuality': u'Standard',
                                            u'StpiShrinkOutput': u'Shrink'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Printer state reasons):
{'printer-state-message': u'Ready to print.',
 'printer-state-reasons': [u'none']}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '1',
                          '_remote_any': '1',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 530925L}
Page 8 (Print test page):
{'test_page_job_status': [], 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [23/Mar/2010:01:32:52 -0400] cupsdSetBusyState: Not busy',
               'D [23/Mar/2010:01:32:52 -0400] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [23/Mar/2010:01:32:52 -0400] cupsdSetBusyState: Active clients',
               'D [23/Mar/2010:01:32:52 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [23/Mar/2010:01:32:52 -0400] cupsdReadClient: 25 1.1 Get-Jobs 1',
               'D [23/Mar/2010:01:32:52 -0400] Get-Jobs ipp://localhost/printers/',
               'D [23/Mar/2010:01:32:52 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [23/Mar/2010:01:32:52 -0400] cupsdSetBusyState: Not busy',
               'D [23/Mar/2010:01:32:52 -0400] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [23/Mar/2010:01:32:52 -0400] cupsdSetBusyState: Active clients',
               'D [23/Mar/2010:01:32:52 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [23/Mar/2010:01:32:52 -0400] cupsdReadClient: 25 1.1 Get-Jobs 1',
               'D [23/Mar/2010:01:32:52 -0400] Get-Jobs ipp://localhost/printers/',
               'D [23/Mar/2010:01:32:52 -0400] [Job 1] Loading attributes...',
               'D [23/Mar/2010:01:32:52 -0400] [Job 2] Loading attributes...',
               'D [23/Mar/2010:01:32:52 -0400] [Job 3] Loading attributes...',
               'D [23/Mar/2010:01:32:52 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [23/Mar/2010:01:32:52 -0400] cupsdSetBusyState: Not busy',
               'D [23/Mar/2010:01:32:52 -0400] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [23/Mar/2010:01:32:52 -0400] cupsdSetBusyState: Active clients',
               'D [23/Mar/2010:01:32:52 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [23/Mar/2010:01:32:52 -0400] cupsdReadClient: 25 1.1 Create-Printer-Subscription 1',
               'D [23/Mar/2010:01:32:52 -0400] Create-Printer-Subscription /',
               'D [23/Mar/2010:01:32:52 -0400] cupsdCreateSubscription(con=0x2140e2f0(25), uri="/")',
               'D [23/Mar/2010:01:32:52 -0400] pullmethod="ippget"',
               'D [23/Mar/2010:01:32:52 -0400] notify-lease-duration=86400',
               'D [23/Mar/2010:01:32:52 -0400] notify-time-interval=0',
               'D [23/Mar/2010:01:32:52 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [23/Mar/2010:01:32:52 -0400] Added subscription 12 for server',
               'D [23/Mar/2010:01:32:52 -0400] cupsdMarkDirty(-----S)',
               'D [23/Mar/2010:01:32:52 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [23/Mar/2010:01:32:52 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [23/Mar/2010:01:32:52 -0400] cupsdSetBusyState: Dirty files',
               'D [23/Mar/2010:01:32:53 -0400] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [23/Mar/2010:01:32:53 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [23/Mar/2010:01:32:53 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [23/Mar/2010:01:32:53 -0400] cupsdReadClient: 25 1.1 Get-Notifications 1',
               'D [23/Mar/2010:01:32:53 -0400] Get-Notifications /',
               'D [23/Mar/2010:01:32:53 -0400] cupsdIsAuthorized: username="brian"',
               'D [23/Mar/2010:01:32:53 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [23/Mar/2010:01:32:53 -0400] cupsdSetBusyState: Dirty files',
               'D [23/Mar/2010:01:32:54 -0400] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [23/Mar/2010:01:32:54 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [23/Mar/2010:01:32:54 -0400] cupsdAuthorize: Authorized as brian using PeerCred',
               'D [23/Mar/2010:01:32:54 -0400] cupsdReadClient: 25 1.1 Cancel-Subscription 1',
               'D [23/Mar/2010:01:32:54 -0400] Cancel-Subscription /',
               'D [23/Mar/2010:01:32:54 -0400] cupsdIsAuthorized: username="brian"',
               'D [23/Mar/2010:01:32:54 -0400] cupsdMarkDirty(-----S)',
               'D [23/Mar/2010:01:32:54 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [23/Mar/2010:01:32:54 -0400] cupsdSetBusyState: Dirty files',
               'D [23/Mar/2010:01:32:55 -0400] cupsdAcceptClient: 26 from localhost (Domain)',
               'D [23/Mar/2010:01:32:55 -0400] cupsdReadClient: 26 GET /admin/log/error_log HTTP/1.1',
               'D [23/Mar/2010:01:32:55 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [23/Mar/2010:01:32:55 -0400] cupsdAuthorize: No authentication data provided.']}
Page 10 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```

---

### Post by thomi_ch on 2010-03-23
Hello

I thin the Problem is pdftopdf:

job-printer-state-message': u'/usr/lib/cups/filter/pdftopdf failed

and

D [21/Mar/2010:23:53:27 -0400] PID 30080 (/usr/lib/cups/filter/pdftopdf) stopped with status 127!

I get this errors to in /var/log/cups/error_log and in the jobqueue for my printer on [http://localhost:631/printers/](http://localhost:631/printers/).

My printer is a Infotec ISC2020... so it's a problem with pdftopdf.

See this bug:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/407344](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/407344)

Some workaround are downgrading to an older cups/libpoppler5, but not helped.

Still have the same problem.. and others too.

Here is a DEBUG error_log:
D [23/Mar/2010:07:51:02 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:02 +0100] cupsdSetBusyState: Not busy
D [23/Mar/2010:07:51:02 +0100] cupsdReadClient: 11 GET /images/unsel.gif HTTP/1.1
D [23/Mar/2010:07:51:02 +0100] cupsdSetBusyState: Active clients
D [23/Mar/2010:07:51:02 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:02 +0100] cupsdSetBusyState: Not busy
D [23/Mar/2010:07:51:02 +0100] cupsdReadClient: 11 GET /images/sel.gif HTTP/1.1
D [23/Mar/2010:07:51:02 +0100] cupsdSetBusyState: Active clients
D [23/Mar/2010:07:51:02 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:02 +0100] cupsdSetBusyState: Not busy
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 11 POST /jobs/ HTTP/1.1
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients
D [23/Mar/2010:07:51:19 +0100] cupsdAuthorize: Authorized as thomi using Basic
D [23/Mar/2010:07:51:19 +0100] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/jobs.cgi"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[10] = "SERVER_ADMIN=root@poseidon"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.1"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[13] = "TZ=Europe/Zurich"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[14] = "USER=root"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[17] = "IPP_PORT=631"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Basic"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[19] = "LANG=en_US.UTF8"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[22] = "SERVER_NAME=localhost"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[23] = "SERVER_PORT=631"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[26] = "SCRIPT_NAME=/jobs/"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/jobs/"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[28] = "REMOTE_USER=thomi"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[29] = "SERVER_PROTOCOL=HTTP/1.1"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[30] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2) Gecko/20100301 Ubuntu/9.10 (karmic) Firefox/3.6"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[31] = "HTTP_REFERER=http://localhost:631/printers/ISC2020"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[32] = "REQUEST_METHOD=POST"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[33] = "CONTENT_LENGTH=63"
D [23/Mar/2010:07:51:19 +0100] [CGI] envp[34] = "CONTENT_TYPE=application/x-www-form-urlencoded"
D [23/Mar/2010:07:51:19 +0100] [CGI] Started /usr/lib/cups/cgi-bin/jobs.cgi (PID 10645)
I [23/Mar/2010:07:51:19 +0100] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=10645)
D [23/Mar/2010:07:51:19 +0100] cupsdSendCommand: 11 file=13
D [23/Mar/2010:07:51:19 +0100] [Job 228] Unloading...
D [23/Mar/2010:07:51:19 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 POST /jobs HTTP/1.1
D [23/Mar/2010:07:51:19 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 1.1 Restart-Job 1
D [23/Mar/2010:07:51:19 +0100] Restart-Job ipp://localhost/jobs/228
D [23/Mar/2010:07:51:19 +0100] [Job 228] Loading attributes...
D [23/Mar/2010:07:51:19 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients and dirty files
I [23/Mar/2010:07:51:19 +0100] [Job 228] Job restarted by user.
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(----J-)
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(----J-)
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:19 +0100] [Job 228] job-sheets=none,none
D [23/Mar/2010:07:51:19 +0100] [Job 228] argv[0]="ISC2020"
D [23/Mar/2010:07:51:19 +0100] [Job 228] argv[1]="228"
D [23/Mar/2010:07:51:19 +0100] [Job 228] argv[2]="anonymous"
D [23/Mar/2010:07:51:19 +0100] [Job 228] argv[3]="Test Page"
D [23/Mar/2010:07:51:19 +0100] [Job 228] argv[4]="1"
D [23/Mar/2010:07:51:19 +0100] [Job 228] argv[5]="job-uuid=urn:uuid:6c2c3bd2-47f3-32fd-4725-f19ea8dc1fd5 job-originating-host-name=localhost"
D [23/Mar/2010:07:51:19 +0100] [Job 228] argv[6]="/var/spool/cups/d00228-001"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[8]="HOME=/var/spool/cups/tmp"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[10]="SERVER_ADMIN=root@poseidon"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[11]="SOFTWARE=CUPS/1.4.1"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[13]="TZ=Europe/Zurich"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[14]="USER=root"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[17]="IPP_PORT=631"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[18]="CHARSET=utf-8"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[19]="LANG=en_US.UTF-8"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[20]="PPD=/etc/cups/ppd/ISC2020.ppd"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[21]="RIP_MAX_CACHE=1014959k"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[23]="DEVICE_URI=socket://172.16.10.101:9100"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[24]="PRINTER_INFO=ISC2020"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[25]="PRINTER_LOCATION=office"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[26]="PRINTER=ISC2020"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[27]="CUPS_FILETYPE=document"
D [23/Mar/2010:07:51:19 +0100] [Job 228] envp[28]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"
I [23/Mar/2010:07:51:19 +0100] [Job 228] Started filter /usr/lib/cups/filter/bannertops (PID 10646)
I [23/Mar/2010:07:51:19 +0100] [Job 228] Started filter /usr/lib/cups/filter/pstopdf (PID 10647)
I [23/Mar/2010:07:51:19 +0100] [Job 228] Started filter /usr/lib/cups/filter/pdftopdf (PID 10648)
I [23/Mar/2010:07:51:19 +0100] [Job 228] Started filter /usr/lib/cups/filter/cpdftocps (PID 10649)
I [23/Mar/2010:07:51:19 +0100] [Job 228] Started backend /usr/lib/cups/backend/socket (PID 10652)
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(-----S)
I [23/Mar/2010:07:51:19 +0100] [Job 228] Restarted by "thomi".
D [23/Mar/2010:07:51:19 +0100] Returning IPP successful-ok for Restart-Job (ipp://localhost/jobs/228) from localhost
D [23/Mar/2010:07:51:19 +0100] [Job 228] load_banner(filename="/var/spool/cups/d00228-001")
D [23/Mar/2010:07:51:19 +0100] [Job 228] Page = 595x842; 12,12 to 583,830
D [23/Mar/2010:07:51:19 +0100] [Job 228] ISC2020: symbol lookup error: ISC2020: undefined symbol: _ZN13GfxColorSpace5parseEP6ObjectP3Gfx
D [23/Mar/2010:07:51:19 +0100] PID 10648 (/usr/lib/cups/filter/pdftopdf) stopped with status 127!
D [23/Mar/2010:07:51:19 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:19 +0100] Script header: Content-Type: text/html;charset=utf-8
D [23/Mar/2010:07:51:19 +0100] Script header: 
D [23/Mar/2010:07:51:19 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:19 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:19 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: +connecting-to-device
D [23/Mar/2010:07:51:19 +0100] [Job 228] Looking up "172.16.10.101"...
D [23/Mar/2010:07:51:19 +0100] [Job 228] Connecting to 172.16.10.101:9100
I [23/Mar/2010:07:51:19 +0100] [Job 228] Connecting to printer...
D [23/Mar/2010:07:51:19 +0100] [Job 228] pdftops argv[5] = 228 anonymous Test Page 1 job-uuid=urn:uuid:6c2c3bd2-47f3-32fd-4725-f19ea8dc1fd5 job-originating-host-name=localhost
D [23/Mar/2010:07:51:19 +0100] [Job 228] PPD: /etc/cups/ppd/ISC2020.ppd
D [23/Mar/2010:07:51:19 +0100] [Job 228] /usr/bin/pdftops supports '-origpagesizes': yes
D [23/Mar/2010:07:51:19 +0100] [Job 228] pstopdf 5 args: 228 anonymous Test Page 1 job-uuid=urn:uuid:6c2c3bd2-47f3-32fd-4725-f19ea8dc1fd5 job-originating-host-name=localhost
D [23/Mar/2010:07:51:19 +0100] [Job 228] PPD: /etc/cups/ppd/ISC2020.ppd
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -connecting-to-device
I [23/Mar/2010:07:51:19 +0100] [Job 228] Connected to printer...
D [23/Mar/2010:07:51:19 +0100] [Job 228] Connected to 172.16.10.101:9100 (IPv4)...
D [23/Mar/2010:07:51:19 +0100] [Job 228] PostScript Level: 2
D [23/Mar/2010:07:51:19 +0100] [Job 228] Duplex: no
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:19 +0100] PID 10645 (/usr/lib/cups/cgi-bin/jobs.cgi) exited with no errors.
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Printing jobs and dirty files
D [23/Mar/2010:07:51:19 +0100] [Job 228] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [23/Mar/2010:07:51:19 +0100] [Job 228] PNG image: 192x128x8, color_type=2 (RGB)
D [23/Mar/2010:07:51:19 +0100] [Job 228] Resolution: 600
D [23/Mar/2010:07:51:19 +0100] PID 10646 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [23/Mar/2010:07:51:19 +0100] [Job 228] ATTR: marker-colors=#000000,none,#00FFFF,#FF00FF,#FFFF00
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(P-----)
D [23/Mar/2010:07:51:19 +0100] [Job 228] ATTR: marker-names="Toner Schwarz","Resttoner 1","Toner Cyan","Toner Magenta","Toner Gelb"
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(P-----)
D [23/Mar/2010:07:51:19 +0100] [Job 228] ATTR: marker-types=toner,wasteToner,toner,toner,toner
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(P-----)
D [23/Mar/2010:07:51:19 +0100] [Job 228] ATTR: marker-levels=-1,-1,-1,-1,-1
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(P-----)
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -media-low-report
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -media-empty-warning
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -toner-low-report
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -toner-empty-warning
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -door-open-report
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -media-jam-warning
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -input-tray-missing-warning
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -output-tray-missing-warning
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -marker-supply-missing-warning
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -output-area-almost-full-report
D [23/Mar/2010:07:51:19 +0100] [Job 228] STATE: -output-area-full-warning
D [23/Mar/2010:07:51:19 +0100] [Job 228] Page size: A4
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:19 +0100] [Job 228] Resolution: 600
D [23/Mar/2010:07:51:19 +0100] [Job 228] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=6, addr=0x7fb9d4c498f8, use_bc=1, side_cb=0x7fb9d393bf60)
D [23/Mar/2010:07:51:19 +0100] [Job 228] Page size: A4
D [23/Mar/2010:07:51:19 +0100] [Job 228] Width: 595, height: 842, absolute margins: 12, 12, 583, 830
D [23/Mar/2010:07:51:19 +0100] [Job 228] Relative margins: 12, 12, 12, 12
D [23/Mar/2010:07:51:19 +0100] [Job 228] PPD options: -level2 -origpagesizes
D [23/Mar/2010:07:51:19 +0100] [Job 228] PostScript to be injected: 
D [23/Mar/2010:07:51:19 +0100] [Job 228] Width: 595, height: 842, absolute margins: 12, 12, 583, 830
D [23/Mar/2010:07:51:19 +0100] [Job 228] Relative margins: 12, 12, 12, 12
D [23/Mar/2010:07:51:19 +0100] [Job 228] PPD options: -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
D [23/Mar/2010:07:51:19 +0100] [Job 228] PostScript to be injected: 
D [23/Mar/2010:07:51:19 +0100] [Job 228] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 - -
D [23/Mar/2010:07:51:19 +0100] [Job 228] Device copies: 1; device collate: 
D [23/Mar/2010:07:51:19 +0100] [Job 228] Running /usr/bin/pdftops  -level2 -origpagesizes /tmp/pdftops.isVgdM -
D [23/Mar/2010:07:51:19 +0100] [Job 228] Running pstops '228' 'anonymous' 'Test Page' '1' ' job-uuid=urn:uuid:6c2c3bd2-47f3-32fd-4725-f19ea8dc1fd5 job-originating-host-name=localhost'
D [23/Mar/2010:07:51:19 +0100] [Job 228] Error: May not be a PDF file (continuing anyway)
D [23/Mar/2010:07:51:19 +0100] [Job 228] Error: PDF file is damaged - attempting to reconstruct xref table...
D [23/Mar/2010:07:51:19 +0100] [Job 228] Error: Couldn't find trailer dictionary
D [23/Mar/2010:07:51:19 +0100] [Job 228] Error: Couldn't read xref table
E [23/Mar/2010:07:51:19 +0100] [Job 228] Empty print file!
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:19 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:19 +0100] PID 10649 (/usr/lib/cups/filter/cpdftocps) stopped with status 1!
D [23/Mar/2010:07:51:19 +0100] [Job 228] GPL Ghostscript 8.70: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [23/Mar/2010:07:51:19 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:19 +0100] Get-Notifications /
D [23/Mar/2010:07:51:19 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:19 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Printing jobs and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [23/Mar/2010:07:51:19 +0100] Get-Job-Attributes ipp://localhost/jobs/228
D [23/Mar/2010:07:51:19 +0100] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/228) from localhost
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Printing jobs and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:19 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:19 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:19 +0100] Get-Notifications /
D [23/Mar/2010:07:51:19 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:19 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Printing jobs and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:19 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:19 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:19 +0100] Get-Notifications /
D [23/Mar/2010:07:51:19 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:19 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Printing jobs and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:19 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:19 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:19 +0100] Get-Notifications /
D [23/Mar/2010:07:51:19 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:19 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Printing jobs and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:19 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:19 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:19 +0100] Get-Notifications /
D [23/Mar/2010:07:51:19 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:19 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:19 +0100] cupsdSetBusyState: Printing jobs and dirty files
D [23/Mar/2010:07:51:19 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:19 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:19 +0100] [Job 228] Error: /ioerror in --showpage--
D [23/Mar/2010:07:51:19 +0100] [Job 228] Operand stack:
D [23/Mar/2010:07:51:19 +0100] [Job 228] 1   true
D [23/Mar/2010:07:51:19 +0100] [Job 228] Execution stack:
D [23/Mar/2010:07:51:19 +0100] [Job 228] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1862   1   3   %oparray_pop   1861   1   3   %oparray_pop   1845   1   3   %oparray_pop   1739   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   1745   0   3   %oparray_pop   --nostringval--   --nostringval--
D [23/Mar/2010:07:51:19 +0100] [Job 228] Dictionary stack:
D [23/Mar/2010:07:51:19 +0100] [Job 228] --dict:1161/1684(ro)(G)--   --dict:0/20(G)--   --dict:128/200(L)--
D [23/Mar/2010:07:51:19 +0100] [Job 228] Current allocation mode is local
D [23/Mar/2010:07:51:19 +0100] [Job 228] Last OS error: 32
D [23/Mar/2010:07:51:19 +0100] [Job 228] GPL Ghostscript 8.70: Unrecoverable error, exit code 1
D [23/Mar/2010:07:51:19 +0100] [Job 228] GPL Ghostscript 8.70: ERROR -12 closing pdfwrite device. See gs/src/ierrors.h for code explanation.
D [23/Mar/2010:07:51:19 +0100] PID 10647 (/usr/lib/cups/filter/pstopdf) stopped with status 1!
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 11 GET /printers/ISC2020 HTTP/1.1
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:24 +0100] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/printers.cgi"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[10] = "SERVER_ADMIN=root@poseidon"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.1"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[13] = "TZ=Europe/Zurich"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[14] = "USER=root"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[17] = "IPP_PORT=631"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[18] = "LANG=en_US.UTF8"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[19] = "REDIRECT_STATUS=1"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[20] = "GATEWAY_INTERFACE=CGI/1.1"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[21] = "SERVER_NAME=localhost"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[22] = "SERVER_PORT=631"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[23] = "REMOTE_ADDR=::1"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[24] = "REMOTE_HOST=localhost"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[25] = "SCRIPT_NAME=/printers/ISC2020"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[26] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/printers/ISC2020"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[27] = "PATH_INFO=/ISC2020"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[28] = "SERVER_PROTOCOL=HTTP/1.1"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[29] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2) Gecko/20100301 Ubuntu/9.10 (karmic) Firefox/3.6"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[30] = "REQUEST_METHOD=GET"
D [23/Mar/2010:07:51:24 +0100] [CGI] envp[31] = "QUERY_STRING="
D [23/Mar/2010:07:51:24 +0100] [CGI] Started /usr/lib/cups/cgi-bin/printers.cgi (PID 10738)
I [23/Mar/2010:07:51:24 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10738)
D [23/Mar/2010:07:51:24 +0100] cupsdSendCommand: 11 file=12
D [23/Mar/2010:07:51:24 +0100] cupsdAcceptClient: 13 from localhost (Domain)
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [23/Mar/2010:07:51:24 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 13 1.1 CUPS-Get-Default 1
D [23/Mar/2010:07:51:24 +0100] CUPS-Get-Default
D [23/Mar/2010:07:51:24 +0100] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [23/Mar/2010:07:51:24 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:24 +0100] [CGI] show_printer(http=0x7fc84accdf20, printer="ISC2020")
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1
D [23/Mar/2010:07:51:24 +0100] Get-Printer-Attributes ipp://localhost/printers/ISC2020
D [23/Mar/2010:07:51:24 +0100] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/ISC2020) from localhost
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [23/Mar/2010:07:51:24 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:24 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:24 +0100] Script header: Content-Type: text/html;charset=utf-8
D [23/Mar/2010:07:51:24 +0100] Script header: 
D [23/Mar/2010:07:51:24 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:24 +0100] [CGI] Regular expression ".*Clean.*"
D [23/Mar/2010:07:51:24 +0100] [CGI] matches[0].rm_so=0
D [23/Mar/2010:07:51:24 +0100] [CGI] matches[1].rm_so=-1
D [23/Mar/2010:07:51:24 +0100] [CGI] Regular expression ".*PrintSelfTestPage.*"
D [23/Mar/2010:07:51:24 +0100] [CGI] matches[0].rm_so=0
D [23/Mar/2010:07:51:24 +0100] [CGI] matches[1].rm_so=-1
D [23/Mar/2010:07:51:24 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 13 1.1 Get-Jobs 1
D [23/Mar/2010:07:51:24 +0100] Get-Jobs ipp://localhost:631/printers/ISC2020
D [23/Mar/2010:07:51:24 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost:631/printers/ISC2020) from localhost
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 13 WAITING Closing on EOF
D [23/Mar/2010:07:51:24 +0100] cupsdCloseClient: 13
D [23/Mar/2010:07:51:24 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:24 +0100] PID 10738 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [23/Mar/2010:07:51:24 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Printing jobs and dirty files
D [23/Mar/2010:07:51:24 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:24 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
I [23/Mar/2010:07:51:24 +0100] [Job 228] Print file sent, waiting for printer to finish...
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:24 +0100] [Job 228] ATTR: marker-levels=-1,-1,-1,-1,-1
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(P-----)
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(-----S)
I [23/Mar/2010:07:51:24 +0100] [Job 228] Ready to print.
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:24 +0100] PID 10652 (/usr/lib/cups/backend/socket) exited with no errors.
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(-----S)
E [23/Mar/2010:07:51:24 +0100] [Job 228] Job stopped due to filter errors; please consult the error_log file for details.
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(----J-)
D [23/Mar/2010:07:51:24 +0100] cupsdMarkDirty(-----S)
D [23/Mar/2010:07:51:24 +0100] [Job 228] The following messages were recorded from 07:51:19 to 07:51:24
D [23/Mar/2010:07:51:24 +0100] [Job 228] hrDeviceDesc="infotec  ISC 2020"
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerColorantValue.1.1 = "black"
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerColorantValue.1.2 = "other"
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerColorantValue.1.3 = "cyan"
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerColorantValue.1.4 = "magenta"
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerColorantValue.1.5 = "yellow"
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerSuppliesLevel.1.1 = -3
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerSuppliesLevel.1.2 = -3
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerSuppliesLevel.1.3 = -3
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerSuppliesLevel.1.4 = -3
D [23/Mar/2010:07:51:24 +0100] [Job 228] prtMarkerSuppliesLevel.1.5 = -3
D [23/Mar/2010:07:51:24 +0100] [Job 228] End of messages
D [23/Mar/2010:07:51:24 +0100] [Job 228] printer-state=3(idle)
D [23/Mar/2010:07:51:24 +0100] [Job 228] printer-state-message="Ready to print."
D [23/Mar/2010:07:51:24 +0100] [Job 228] printer-state-reasons=none
D [23/Mar/2010:07:51:24 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:24 +0100] Get-Notifications /
D [23/Mar/2010:07:51:24 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:24 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:24 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:24 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:24 +0100] Get-Notifications /
D [23/Mar/2010:07:51:24 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:24 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:24 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:24 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:24 +0100] Get-Notifications /
D [23/Mar/2010:07:51:24 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:24 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:24 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:24 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [23/Mar/2010:07:51:24 +0100] Get-Notifications /
D [23/Mar/2010:07:51:24 +0100] cupsdIsAuthorized: requesting-user-name="thomi"
D [23/Mar/2010:07:51:24 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [23/Mar/2010:07:51:24 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:24 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [23/Mar/2010:07:51:24 +0100] cupsdCloseClient: 12
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 11 GET /printers/ISC2020 HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/printers.cgi"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[10] = "SERVER_ADMIN=root@poseidon"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.1"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[13] = "TZ=Europe/Zurich"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[14] = "USER=root"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[17] = "IPP_PORT=631"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[18] = "LANG=en_US.UTF8"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[19] = "REDIRECT_STATUS=1"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[20] = "GATEWAY_INTERFACE=CGI/1.1"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[21] = "SERVER_NAME=localhost"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[22] = "SERVER_PORT=631"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[23] = "REMOTE_ADDR=::1"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[24] = "REMOTE_HOST=localhost"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[25] = "SCRIPT_NAME=/printers/ISC2020"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[26] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/printers/ISC2020"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[27] = "PATH_INFO=/ISC2020"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[28] = "SERVER_PROTOCOL=HTTP/1.1"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[29] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2) Gecko/20100301 Ubuntu/9.10 (karmic) Firefox/3.6"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[30] = "REQUEST_METHOD=GET"
D [23/Mar/2010:07:51:34 +0100] [CGI] envp[31] = "QUERY_STRING="
D [23/Mar/2010:07:51:34 +0100] [CGI] Started /usr/lib/cups/cgi-bin/printers.cgi (PID 10747)
I [23/Mar/2010:07:51:34 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10747)
D [23/Mar/2010:07:51:34 +0100] cupsdSendCommand: 11 file=12
D [23/Mar/2010:07:51:34 +0100] Report: clients=1
D [23/Mar/2010:07:51:34 +0100] Report: jobs=168
D [23/Mar/2010:07:51:34 +0100] Report: jobs-active=1
D [23/Mar/2010:07:51:34 +0100] Report: printers=2
D [23/Mar/2010:07:51:34 +0100] Report: printers-implicit=0
D [23/Mar/2010:07:51:34 +0100] Report: stringpool-string-count=2855
D [23/Mar/2010:07:51:34 +0100] Report: stringpool-alloc-bytes=16368
D [23/Mar/2010:07:51:34 +0100] Report: stringpool-total-bytes=55416
D [23/Mar/2010:07:51:34 +0100] cupsdAcceptClient: 13 from localhost (Domain)
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 13 1.1 CUPS-Get-Default 1
D [23/Mar/2010:07:51:34 +0100] CUPS-Get-Default
D [23/Mar/2010:07:51:34 +0100] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] [CGI] show_printer(http=0x7f19019fff20, printer="ISC2020")
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 13 1.1 Get-Printer-Attributes 1
D [23/Mar/2010:07:51:34 +0100] Get-Printer-Attributes ipp://localhost/printers/ISC2020
D [23/Mar/2010:07:51:34 +0100] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/ISC2020) from localhost
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:34 +0100] Script header: Content-Type: text/html;charset=utf-8
D [23/Mar/2010:07:51:34 +0100] Script header: 
D [23/Mar/2010:07:51:34 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:34 +0100] [CGI] Regular expression ".*Clean.*"
D [23/Mar/2010:07:51:34 +0100] [CGI] matches[0].rm_so=0
D [23/Mar/2010:07:51:34 +0100] [CGI] matches[1].rm_so=-1
D [23/Mar/2010:07:51:34 +0100] [CGI] Regular expression ".*PrintSelfTestPage.*"
D [23/Mar/2010:07:51:34 +0100] [CGI] matches[0].rm_so=0
D [23/Mar/2010:07:51:34 +0100] [CGI] matches[1].rm_so=-1
D [23/Mar/2010:07:51:34 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 13 1.1 Get-Jobs 1
D [23/Mar/2010:07:51:34 +0100] Get-Jobs ipp://localhost:631/printers/ISC2020
D [23/Mar/2010:07:51:34 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost:631/printers/ISC2020) from localhost
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 13 WAITING Closing on EOF
D [23/Mar/2010:07:51:34 +0100] cupsdCloseClient: 13
D [23/Mar/2010:07:51:34 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:34 +0100] PID 10747 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [23/Mar/2010:07:51:34 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:34 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:34 +0100] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 11 GET /cups.css HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 11 GET /images/left.gif HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 11 GET /images/right.gif HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 11 GET /images/unsel.gif HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdReadClient: 11 GET /images/sel.gif HTTP/1.1
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Active clients and dirty files
D [23/Mar/2010:07:51:34 +0100] cupsdAuthorize: No authentication data provided.
D [23/Mar/2010:07:51:34 +0100] cupsdSetBusyState: Dirty files


We need a FIX..

thomi

---

### Post by hart02 on 2010-03-23
> I thin the Problem is pdftopdf:

job-printer-state-message': u'/usr/lib/cups/filter/pdftopdf failed

and

D [21/Mar/2010:23:53:27 -0400] PID 30080 (/usr/lib/cups/filter/pdftopdf) stopped with status 127!

I get this errors to in /var/log/cups/error_log and in the jobqueue for my printer on [http://localhost:631/printers/](http://localhost:631/printers/).

My printer is a Infotec ISC2020... so it's a problem with pdftopdf.

See this bug:
[https://bugs.launchpad.net/ubuntu/+s...ps/+bug/407344](https://bugs.launchpad.net/ubuntu/+s...ps/+bug/407344)

the pdftopdf file is also the culprit for me as well. I went to the link provided. It's says there is a fix released but i can't where it says how to fix it.

---

