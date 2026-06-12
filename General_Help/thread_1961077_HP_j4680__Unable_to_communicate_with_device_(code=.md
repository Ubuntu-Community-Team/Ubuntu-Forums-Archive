---
title: "HP j4680  Unable to communicate with device (code=12): hp:/usb/Officejet_J4680_series"
date: 2012-04-18
forum: General Help
---

### Post by myBunt47 on 2012-04-18
Hi,

my print driver don't wort since serveral day :-(

KDE 4.8.2.
Kubuntu 11.10.

I try follow:

> 
hp-info

its open a window with following messag:


Unable to open device hp:/usb/Officejet_J4680_series?serial=CN9CHD521V052X



After the command:

hp-probe

HP Linux Imaging and Printing System (ver. 3.12.4)
Printer Discovery Utility ver. 4.1

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                              
            Type                                                                 
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                               
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)

Enter number 0...1 for connection type (q=quit, enter=usb*) ? 0

Using connection type: usb


--------------------
| DEVICE DISCOVERY |
--------------------

warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
warning: check to make sure your devices are properly connected and powered on.

Done.


and:
> 
hp-scan

HP Linux Imaging and Printing System (ver. 3.12.4)
Scan Utility ver. 2.2

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hpaio:/usb/Officejet_J4680_series?serial=CN9CHD521V052X

warning: No destinations specified. Adding 'file' destination by default.
error: Unable to locate device hpaio:/usb/Officejet_J4680_series?serial=CN9CHD521V052X using SANE backend hpaio:. Please check HPLIP installation.


> 
sudo apt-get install --assume-yes xsane
[sudo] password for myUser: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
xsane ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

google translate:
> 
Reading package lists ... ready
Dependency tree
Status information is read ... ready
xsane is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


> 
xsane -v
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
xsane-0.998 © 1998-2010 Oliver Rauch
  E-Mail: [email]Oliver.Rauch@xsane.org[/email]
  Paket xsane-0.996
  übersetzt mit GTK-2.24.5
  mit Farbmanagement-Funktion
  mit GIMP-Unterstützung, übersetzt mit GIMP-2.6.11
  XSane Ausgabeformate: jpeg, pdf(compr.), png, pnm, ps(compr.), tiff, txt



and I kown, that my printer don't have conneciton to my computer :-(
But how can he connecting my compunter?
Can someone halp my?

Thanks in advance

Sorry my english.

regards
mybuntu

---

