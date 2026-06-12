---
title: "HP Photosmart Premium Wireless [Lubuntu]"
date: 2012-05-12
forum: General Help
---

### Post by momist on 2012-05-12
Hello everyone. 
I'm having some difficulty with getting my printer to work with Lubuntu 12.04 Precise.  In Ubuntu it's pretty easy, if long winded, just following the instructions from [http://hplipopensource.com](http://hplipopensource.com)

I have done exactly the same in Lubuntu, and given lack of any other choice, when the instructions ask what Linux distribution I'm using I gave it Ubuntu.  Everything about the install went normally until I got a message saying "/usr/lib/cups/filter/gstoraster failed".  The install then completed normally.

Once finished, I had to re-run hp-setup a second time, and then in the Lubuntu printer control I had to make the printer shared.  The system can see the printer on the network, but still has the status flagged as:  "/usr/lib/cups/filter/gstoraster failed".

I have a cups log which includes the following:
```
  ['\x1b[35;01mwarning: No display found.\x1b[0m',
                   '\x1b[31;01merror: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.\x1b[0m',
                   "WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-mZ4Gmq/pkcs11: No such file or directory",
                   '\x1b[31;01merror: Unable to communicate with device (code=12): hp:/net/Photosmart_Prem_C310_series?zc=HPCEA98E\x1b[0m',
                   '\x1b[31;01merror: Error opening device (Device not found).\x1b[0m',
                   ''],
                  0),
```
and also the following:
```
{'error_log': ['D [11/May/2012:23:54:45 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [11/May/2012:23:54:45 +0100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [11/May/2012:23:54:45 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [11/May/2012:23:54:45 +0100] cupsdAuthorize: No authentication data provided.',
               'D [11/May/2012:23:54:45 +0100] cupsdReadClient: 14 1.1 Get-Jobs 1',
               'D [11/May/2012:23:54:45 +0100] Get-Jobs ipp://localhost/printers/',
               'D [11/May/2012:23:54:45 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [11/May/2012:23:54:45 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [11/May/2012:23:54:45 +0100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [11/May/2012:23:54:45 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [11/May/2012:23:54:45 +0100] cupsdAuthorize: No authentication data provided.',
               'D [11/May/2012:23:54:45 +0100] cupsdReadClient: 14 1.1 Get-Jobs 1',
               'D [11/May/2012:23:54:45 +0100] Get-Jobs ipp://localhost/printers/',
               'D [11/May/2012:23:54:45 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [11/May/2012:23:54:45 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [11/May/2012:23:54:45 +0100] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [11/May/2012:23:54:45 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [11/May/2012:23:54:45 +0100] cupsdAuthorize: No authentication data provided.',
               'D [11/May/2012:23:54:45 +0100] cupsdIsAuthorized: username=""',
               'D [11/May/2012:23:54:45 +0100] cupsdSendHeader: 14 WWW-Authenticate: Basic realm="CUPS", trc="y"',
               'D [11/May/2012:23:54:45 +0100] cupsdCloseClient: 14',
               'D [11/May/2012:23:54:45 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [11/May/2012:23:54:45 +0100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [11/May/2012:23:54:45 +0100] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [11/May/2012:23:54:45 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [11/May/2012:23:54:45 +0100] cupsdAuthorize: Authorized as ian using PeerCred',
               'D [11/May/2012:23:54:45 +0100] cupsdIsAuthorized: username="ian"',
               'I [11/May/2012:23:54:45 +0100] Installing config file "/etc/cups/cupsd.conf"...',
               'D [11/May/2012:23:54:46 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [11/May/2012:23:54:46 +0100] cupsdCloseClient: 14',
               'D [11/May/2012:23:54:46 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"',
               'D [11/May/2012:23:54:46 +0100] cupsdDeregisterPrinter(p=0x7f3397b05f10(Photosmart_Prem_C310), removeit=1)',
               'I [11/May/2012:23:54:46 +0100] Generating printcap /var/run/cups/printcap...',
               'D [11/May/2012:23:54:46 +0100] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"',
               'W [11/May/2012:23:54:46 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files',
               'W [11/May/2012:23:54:46 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files',
               'W [11/May/2012:23:54:46 +0100] failed to CreateDevice: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files'],
 'error_log_debug_logging_unset': True}
Page 10 (Locale issues):
{'printer_page_size': u'A4.Duplex',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_GB',
 'user_locale_messages': 'en_GB'}
```

Can anyone suggest what I should do next please?

Thanks,

---

### Post by momist on 2012-05-12
SOLVED

Sorry if I have wasted anyone's time on this.  Simply my stupidity, I'm afraid.
It seems all that was required was to delete the printer, and then start again with add printer, and it then picked up the keyring thing correctly and it works.

Hope that helps someone else.

Ian

---

