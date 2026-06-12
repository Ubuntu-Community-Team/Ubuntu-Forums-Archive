---
title: "Need help installing printer"
date: 2010-11-07
forum: General Help
---

### Post by relik0fages on 2010-11-07
I just bought a new HP LaserJet CP1525nw color. Ubuntu detects that it is on the network and I can see it. But when I try to connect to it, it says cannot find drivers. Any help would be greatly appreciated. I just spent an arm and leg for this. Thank You in advance.

Ubuntu 10.04 
kernel 2.6.32-25
GNOME 2.30.2

---

### Post by kanishkdudeja on 2010-11-07
u will have to download hplip

```
sudo apt-get update && sudo apt-get install hplip
```

---

### Post by relik0fages on 2010-11-07
Thank you for helping, but i currently have that package installed. Even before gettting the printer. Anything else would be great help.

---

### Post by kanishkdudeja on 2010-11-07
okay..when u plug in the printer doesnt it ask u whether to install the plugin or not ?

---

### Post by relik0fages on 2010-11-07
When i plug in the printer it says "Searching for drivers" and it lists the printer im connected to. Then it pauses and start a few times. then says "Printer Drivers Not Found" then a dialog pops up asking me to use a "Select printer from database,provide a ppd, or Search for a printer driver to download." all have failed to find a proper driver.

---

### Post by Mark Phelps on 2010-11-07
Go into Synaptic Package Manager and install cups-driver-gutenprint -- and any other packages it requests as a side-effect.

Then, open a browser to "localhost:631".  This will load CUPS into your browser.

Use the feature to add a printer and look through the Gutenprint driver list to see if there is one for your printer.

I print to HP printers and have found the Gutenprint drivers to be excellent!

---

### Post by relik0fages on 2010-11-07
I actually ended up fixing it earlier today. I installed a driver hp cp1515n(previous model driver.) And it works fine. Now only if every company started support linux with up-to-date drivers i'd be in my glory. Thanks for the help.

---

