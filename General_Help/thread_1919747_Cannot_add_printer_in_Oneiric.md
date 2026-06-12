---
title: "Cannot add printer in Oneiric"
date: 2012-02-03
forum: General Help
---

### Post by Arfalarf on 2012-02-03
I am trying to add a network printer that I have the IP address for.  I go to applications->system tools->system settings->printers, which seems like it should allow me to add a printer.  I click on the little plus sign in the lower left corner to add a printer, and nothing happens.  It simply does not acknowledge my mouse click.  How can I fix this, or alternately, how can I add the printer from the command line?

---

### Post by imachavel on 2012-02-03
I myself have a host based printer that I use, not a network printer. My printer is an old HP laser jet 1012, that windows 7 no longer provides drivers for. In ubuntu though, my printer had drivers automatically compiled and read for the printer. It was automatically detected and worked. Of course I'm using a host based printer, and not a network printer. Let me get back to you though, I'll edit this in a second


sudo system-config-printer

[http://www.edwardstafford.com/2009/08/31/add-a-network-printer-to-an-ubuntu-desktop-the-easy-way/](http://www.edwardstafford.com/2009/08/31/add-a-network-printer-to-an-ubuntu-desktop-the-easy-way/)

Press the &#8220;**New**&#8221; button to add a new printer.
 The &#8220;**New Printer**&#8221; window will open after a brief search displaying the &#8220;select Device&#8221; panel
 Under the &#8220;Devices&#8221; list, expand the &#8220;**Network Printer**&#8221; selection by clicking the small black arrow.
 Next, Select &#8220;**AppSocket/HP JetDirect**&#8221;
 At the right, new options will be displayed (Host and Port Number)
 In the host field, type the IP address of the network printer you&#8217;re installing.

---

### Post by Arfalarf on 2012-02-03
Thanks, that's exactly what I was looking for.

---

