---
title: "Printing to HP Design Jet 800 Plotter"
date: 2011-08-10
forum: General Help
---

### Post by rhugga on 2011-08-10
Anyone know if this printer is usable with 11.0.4?

I was able to add the plotter (via jetdirect) and print a test page, however I can't get any applications to print. I don't get an errors, I don't see anything stuck in my local print queue and when I got to the printer it has no pending jobs.

Also for some reason using hp-setup would not work for this printer as it has for other HP printers.

I tried:

hp-setup -i <ip address>

root:~# hp-setup -i 192.168.1.100

HP Linux Imaging and Printing System (ver. 3.11.1)
Printer/Fax Setup Utility ver. 9.0
<snip>

--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)
  2         par         Parallel Port (LPT:)                                      

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 1

Using connection type: net

-
error: Invalid device URI: 

Thanks for any info,

---

