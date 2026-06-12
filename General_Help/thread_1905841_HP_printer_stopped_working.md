---
title: "HP printer stopped working"
date: 2012-01-07
forum: General Help
---

### Post by majoob on 2012-01-07
Our HP Deskjet 5440 has stopped printing. 
It has something to do with the Printer State:
```
stopped -/usr/lib/cups/backend/hp failed
```
But I don't know how to fix this.
[IMG]http://dl.dropbox.com/u/3655335/printer_properties.png[/IMG]
It's USB connection is ok because I can use HP Device Manager to both clean the print cartridges and align them (where it does prints test alignment pages). However printing a test page doesn't work (does nothing ... no error message).

Ubuntu 11.10 32 bit

I'd appreciate any help.

---

### Post by bluexrider on 2012-01-07
Unplug the printer from the USB. Reboot and plug it back in. 

If that doesn't work then ```
sudo rm -f /usr/lib/cups/backend/hp
```

and try again

---

### Post by majoob on 2012-01-09
unplug - reboot - plug didn't work, so I removed /usr/lib/cups/backend/hp and rebooted.

Now I get error messages about the print queue and the printer is looking for that deleted hp file.

The printing troubleshooter gave the message: 
[I]Queue Not Enabled
The queue 'Desktop-5400-series' is not enabled. The reason given is: 'Backend /usr/lib/cups/backend/hp does not exist!'.

To enable it, select the 'Enabled' checkbox in the 'Policies' tab for the printer in the printer administration tool. To start this tool, select System->Administration->Printing from the main menu. [/I]

I did this, but the hp file wasn't created.

Anyone know how to fix this?

---

### Post by bluexrider on 2012-01-09
should probably have suggested this before

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

reinstall 'hplip' from HP

HPLIP is also available in the repositories and HPLIP Toolbox is there too

---

### Post by majoob on 2012-01-09
> reinstall 'hplip' from HP

HPLIP is also available in the repositories and HPLIP Toolbox is there too 

That did the trick. Thanks for your help!

---

### Post by bluexrider on 2012-01-10
Glad to help out

---

