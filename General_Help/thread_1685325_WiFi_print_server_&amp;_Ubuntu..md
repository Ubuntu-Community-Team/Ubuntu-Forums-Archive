---
title: "WiFi print server &amp; Ubuntu."
date: 2011-02-10
forum: General Help
---

### Post by yerayenrique on 2011-02-10
Hi there,

Im looking for some help on the following:

I have a Canon MP250 (multi) which works perfectly (both scanner and printer) with Ubu10.04 through USB.

Thing's that I've now received a discontinued D-Link DP-311U ([http://www.dlink.com/products/?pid=38](http://www.dlink.com/products/?pid=38)) print server and, since every time I had to print I had to change room and connect to the USB, I'd love to have it working. BUT I'm completely lost with WiFi print servers.

I assume the connections I just need to connect the printer to the WiFi print server via USB and that's it, right? It's WiFi, I shouldn't have to connect it to my router.

Again, I'm very lost at this so please feel free to correct me.

Could you help me out a little?

Many thanks!

---

### Post by Mark Phelps on 2011-02-10
I have an HP printer working through WiFi, a print server, and Ubuntu 10.10.

I installed the printer by using CPUS (localhost:631 in your browser) and using the option to detect network printers.  CUPS found it without problems.

---

### Post by yerayenrique on 2011-02-10
> **Mark Phelps said:**
> I have an HP printer working through WiFi, a print server, and Ubuntu 10.10.

I installed the printer by using CPUS (localhost:631 in your browser) and using the option to detect network printers.  CUPS found it without problems.

I've been investigating CUPS (didn't know about it) but I don't seem to find a way to do this.

Could you explain?

---

### Post by Mark Phelps on 2011-02-11
Enter localhost:631 in your browser.  That will open the CUPS home screen.

Look around and you will find the option to add a printer.  It may be under Manage Printers. Choose that.

It will have options for local and network printers.

If you select the network printer option, it should search your network and if the printer is connected via wireless to the network, it should find it and list it for you.

You then choose that printer and follow the menus to select the appropriate driver.

---

