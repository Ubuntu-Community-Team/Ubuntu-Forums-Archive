---
title: "Printer not found"
date: 2011-11-04
forum: General Help
---

### Post by cocokessler on 2011-11-04
I am using **l**ubuntu 11.10, and it cannot see my uPnP USB printer, an HP psc 750 all-in-one. The last 3 or 4 releases of **U**buntu find the printer automatically and print to it without problems. 

This is a data file that was generated during unsuccessful attempt to "find printer":

[quote=""]Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': False}
Page 4 (Choose device):
{'cups_device_listed': False, 'cups_devices_available': {}}
Page 5 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}[/quote] 

Thank you ahead of time for your help!

---

### Post by DapperMe17 on 2011-11-04
Assuming that you've tried to unplug/replug your USB connection, maybe you can install HPLIP-GUI (HP Toolbox), restart CUPS and try again?wiaawiaa

---

### Post by amjjawad on 2011-11-05
> **cocokessler said:**
> I am using **l**ubuntu 11.10, and it cannot see my uPnP USB printer, an HP psc 750 all-in-one. The last 3 or 4 releases of **U**buntu find the printer automatically and print to it without problems. 

This is a data file that was generated during unsuccessful attempt to "find printer":

 

Thank you ahead of time for your help!

Hi :)

Kindly connect your Printer and from LXTerminal, please run this command:

```
lsusb
```

Please post the output here and wrap up the text with [CODE] Tags.

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]


Thank you!

---

