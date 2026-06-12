---
title: "Unable to print after upgrading to 12.04"
date: 2012-05-03
forum: General Help
---

### Post by seawright on 2012-05-03
I was unable to print after upgrading to 12.04.
Printing worked fine before upgrading and I have not made any changes to the configuration.

Anything I try to print goes into the print queue where it is reported as stopped.

The printer is an Epson Stylus Color 500 connected to /dev/lp0

As far as I am aware all the correct kernel modules are loaded:
parport,ppdev,parport_pc & lp

There is communication through the port as the "Clean Print Heads" button
on the settings sheet of printer properties does initiate a head cleaning cycle.

Selected driver is "Epson Stylus Color 500 - CUPS+Gutenprint v5.2.7 Simplified" only other option available in Foomatic printer database is "Epson Stylus Color 500 Foomatic/stcolor [en]"

Changing drivers but retaining existing settings restored printing but print quality was poor. Reverting to original driver restored status quo.

As fault no longer exists I am unable to investigate further as to why distribution upgrade caused a problem as I usually upgrade when a new version becomes available but this is the first time it has caused printing problems.

It would be interesting to know if anyone else has had printer problems when upgrading.

---

### Post by phil smart on 2012-05-17
Hi there Yes I have still got problems after 12.04 update. My Epson585 will not print direct to cd eg if printing cd labels. The job just hangs saying "processing". All jobs to this printer stopped for a while but on changing the driver from gutenprint5.2.8 to any other driver than back to the original 5.2.8 paper jobs print but the direct to cd tray is still not working

I run mint12 as well and the driver on mint 12 is gutenprint 5.2.7 which works fine to paper and the Cd

I have tried to find a gutenprint 5.2.7 for Ubuntu 12.04 but none listed.

I can't believe that after a major update to LTS printing is so badly effected.

---

### Post by geomcd1949 on 2012-05-18
I too am having problems after upgrading to 12.04. Now all my print jobs end up in qeue, where it says they are "Processing." But nothing ever happens after that.

---

### Post by notquitestr8t on 2012-05-19
I have an Epson ip4700. Same story. Status is "Idle-sending data to printer" but nothing happens. The message states: "There was an error during the CUPS operation: 'server-error-internal-error'."
I ran through the troubleshooting guide and got the debug info.  I deleted it and reinstalled but get the same thing. Below is a partial from the debug b ut I am not sure what it means.

'D [19/May/2012:07:07:32 -0500] cupsdCloseClient: 22',
               'D [19/May/2012:07:07:32 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"',
               'D [19/May/2012:07:07:32 -0500] cupsdCloseClient: 23',
               'D [19/May/2012:07:07:32 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"',
               'D [19/May/2012:07:07:32 -0500] cupsdCloseClient: 17',
               'D [19/May/2012:07:07:32 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"',
               'D [19/May/2012:07:07:32 -0500] cupsdDeregisterPrinter(p=0x7f1f1affcd70(iP4700-series), removeit=1)',
               'I [19/May/2012:07:07:32 -0500] Saving subscriptions.conf...',
               'D [19/May/2012:07:07:32 -0500] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"',
               "W [19/May/2012:07:07:32 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'iP4700-series-Gray..' already exists",
               "W [19/May/2012:07:07:32 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'iP4700-series-RGB..' already exists",
               "W [19/May/2012:07:07:32 -0500] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-iP4700-series' already exists",
               'E [19/May/2012:07:07:32 -0500] Failed to update TXT record for Canon iP4700 series @ colson-desktop: -2'],
 'error_log_debug_logging_unset': True}
Page 10 (Printer state reasons):
{'printer-state-message': u'Sending data to printer.',
 'printer-state-reasons': [u'none']}
Page 11 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by n.brenner on 2012-05-19
The problem is with CUPS and their upgrade from 1.4.4 to 1.5.0+
But the word doesn't seem to have reached them.

I have a problem with an Oce' fx3000 laser jet.

everything installs , etc, but all I get is "cups-ipp-wrong-http-version"

everything worked befor in 10.10 and 11.04...(mint 10 and mint 11)

I suscribe to "IF IT AINT BROKE, DON'T FIX IT"

How can I degrade CUPS to 1.4.4

---

### Post by phil smart on 2012-07-10
I also run mint. When in mint 12 all ok with printing on my epson photo 585 now I have booted in to Mint 13 ( based on U12.04) printing to cd tray fails.
Surely more than 4 people  out there have had the same problem

I reported this error on the mint forum but no luck yet
Thanks
Phil

---

### Post by spametki on 2012-08-08
[QUOTE=phil smart;11943186]Hi there Yes I have still got problems after 12.04 update. My Epson585 will not print direct to cd eg if printing cd labels. The job just hangs saying "processing"

The same problem with this config:

Last Ubuntu desktop i386 with complete packages update
Default distribution Epson TX110 driver
Epson TX 115 printer/scanner

The printer stops before ending the print job (stays idle with intermitent green light), but the system printing pool is empty.

---

### Post by broonsparrow on 2012-09-02
Hi,

I;ve just upgraded to 12.04 and am unable to print on my Epson Photo R300 - is this solved yet?

---

