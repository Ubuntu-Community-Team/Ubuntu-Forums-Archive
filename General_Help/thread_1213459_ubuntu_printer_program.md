---
title: "ubuntu printer program?"
date: 2009-07-14
forum: General Help
---

### Post by user sam on 2009-07-14
I have an old computer and an old printer. Since I started from a base install I don't have the ubuntu program for setting up printers(the one that is under system>administration>printing). Does anyone know what its name is so I can apt-get install it?

---

### Post by oldos2er on 2009-07-14
system-config-printer-common - Printer configuration GUI
system-config-printer-gnome - Printer configuration GUI

---

### Post by user sam on 2009-07-15
Thanks, that was going to drive me berserk.

---

### Post by Cheesemill on 2009-07-15
You can search for packages using aptitude:
```
aptitude search printer
```gives the following results:
```
p   ebox-printers                                  - eBox - Printer sharing                                   
p   gnome-photo-printer                            - tool for Gnome to print several photos on one page       
p   kde-printer-applet                             - printer status applet                                    
p   libprinterconf-dev                             - Printer autodetection library                            
p   libprinterconf0c2a                             - Printer autodetection library                            
i   system-config-printer-common                   - Printer configuration GUI                                
i   system-config-printer-gnome                    - Printer configuration GUI                                
p   system-config-printer-kde                      - Printer Status Applet                                    

```

---

