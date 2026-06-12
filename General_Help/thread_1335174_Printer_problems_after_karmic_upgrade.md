---
title: "Printer problems after karmic upgrade"
date: 2009-11-23
forum: General Help
---

### Post by gotanothergrot on 2009-11-23
I have a hp1020 lazerjet that has been working fine until  upgraded to karmic.
However the printer tells me its not connected or processing.:icon_frown:

---

### Post by blazemore on 2009-11-23
Please run the command
```
hp-info
```

And paste here what it says.

Thanks!

---

### Post by gotanothergrot on 2009-11-23
graham@graham-desktop:~$ hp-info

HP Linux Imaging and Printing System (ver. 3.9.8)
Device Information Utility ver. 5.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.
Using device: hp:/usb/HP_LaserJet_1020?serial=JL3PSXZ


HP Linux Imaging and Printing System (ver. 3.9.8)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.
warning: Unable to connect to dbus. Is hp-systray running?

hp:/usb/HP_LaserJet_1020?serial=JL3PSXZ

error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_1020?serial=JL3PSXZ
error: Error opening device (Device not found).
Device Parameters (dynamic data):
  Parameter                     Value(s)                                                  
  ----------------------------  ----------------------------------------------------------
  back-end                      hp                                                        
  cups-printers                 HP_LaserJet_1020                                          
  cups-uri                      hp:/usb/HP_LaserJet_1020?serial=JL3PSXZ                   
  dev-file                                                                                
  device-state                  -1                                                        
  device-uri                    hp:/usb/HP_LaserJet_1020?serial=JL3PSXZ                   
  deviceid                                                                                
  error-state                   101                                                       
  host                                                                                    
  is-hp                         True                                                      
  panel                         0                                                         
  panel-line1                                                                             
  panel-line2                                                                             
  port                          1                                                         
  serial                        JL3PSXZ                                                   
  status-code                   5002                                                      
  status-desc                                                                             

Model Parameters (static data):
  Parameter                     Value(s)                                                  
  ----------------------------  ----------------------------------------------------------
  align-type                    0                                                         
  clean-type                    0                                                         
  color-cal-type                0                                                         
  copy-type                     0                                                         
  embedded-server-type          0                                                         
  fax-type                      0                                                         
  fw-download                   True                                                      
  icon                          HP_LaserJet_1012.png                                      
  io-mfp-mode                   6                                                         
  io-mode                       1                                                         
  io-support                    2                                                         
  job-storage                   0                                                         
  linefeed-cal-type             0                                                         
  model                         HP_LaserJet_1020                                          
  model-ui                      HP LaserJet 1020                                          
  model1                        HP LaserJet 1020 Printer                                  
  model2                        HP LaserJet 1020 Plus Printer                             
  monitor-type                  0                                                         
  panel-check-type              0                                                         
  pcard-type                    0                                                         
  plugin                        1                                                         
  plugin-reason                 1                                                         
  power-settings                0                                                         
  pq-diag-type                  0                                                         
  r-type                        0                                                         
  r0-agent1-kind                4                                                         
  r0-agent1-sku                 Q2612A                                                    
  r0-agent1-type                1                                                         
  scan-style                    0                                                         
  scan-type                     0                                                         
  status-battery-check          0                                                         
  status-dynamic-counters       0                                                         
  status-type                   8                                                         
  support-released              True                                                      
  support-subtype               14304                                                     
  support-type                  2                                                         
  support-ver                   2.7.10                                                    
  tech-class                    ['LJZjsMono']                                             
  tech-subclass                 ['Normal']                                                
  tech-type                     3                                                         
  usb-pid                       11031                                                     
  usb-vid                       1008                                                      
  wifi-config                   0                                                         

Done.
graham@graham-desktop:~$

---

### Post by blazemore on 2009-11-23
Hit Alt+F2 and type
```
hp-systray
```
Then press Enter.

---

### Post by gotanothergrot on 2009-11-23
Oh dear.

---

### Post by blazemore on 2009-11-23
OK.
Go here, follow the wizard and download and install the file.
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

---

### Post by gotanothergrot on 2009-11-23
OK  Thanks.

---

### Post by blazemore on 2009-11-23
Did it work?

---

### Post by gotanothergrot on 2009-11-23
I went through the process thus far, however my system is not detecting the printer.

---

### Post by XubuRoxMySox on 2009-11-23
Try this: Open a browser and go to [http://localhost:631/](http://localhost:631/)

Click on the **Administration** tab and see if it lists your printer as being installed. If not, select **Add Printer** (you will be prompted for your computer login and password) and select from the list that appears. It will add the correct PPA for you.

-Robin

---

### Post by gotanothergrot on 2009-11-23
I just got my computer back, some real bad weather just hit us I thought a small tornado was hitting, very scary.

Have I lost the stuff I done in the terminal after a power failure?

Will follow your advice dixiedancer

---

### Post by gotanothergrot on 2009-11-23
How do you do it:p

:D:D: All sorted now Thanks dixiedancer thanks blazemore :D:D

---

### Post by gotanothergrot on 2009-11-23
Just one more thing!!

What do I do with the hplip downloads that were saved to and are still on  my desktop? (center)

---

### Post by blazemore on 2009-11-23
You can safely delete them

---

