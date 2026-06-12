---
title: "Installing Network Printer (HP Color Laser Jet 2605dn)"
date: 2010-01-08
forum: General Help
---

### Post by Black_Moon on 2010-01-08
I've HP Color Laser Jet 2605dn printer in network (IP: 192.168.0.103).
Printer instaled successfully using CUPS. I can print from this Linux machine.

Now I need to print on HP CLJ 2605dn from Windows machines. 
If I put printer driver myself from Windows printer installation it works.
But if I try to use printer from Linux it reports that there's no driver.

So I forced to use Samba to include in Linux share Windows HP driver.

I copyed **cups-windows 6.0 drivers** into /usr/share/cups/drivers
and also
> 
ps5ui.dll 
pscript5.dll
pscript.hlp
pscript.ntf
Then run - 
> [B]
cupsaddsmb -U root -a -V[/B]
If > 
[global]
   load printers = yes
   printing = cups
   printcap name = cups
   security = share
returns [B]tree connect failed: NT_STATUS_WRONG_PASSWORD
[/B]If > 
[global]
   load printers = yes
   printing = cups
   printcap name = cups
            security = user
returns [B]tree connect failed: NT_STATUS_ACCESS_DENIED


[/B]There's mistake?

p.s. smb.conf file in attachement.

---

### Post by pricetech on 2010-01-08
Maybe I'm lost in the confusion, but;

If it's a network printer, are you trying to print directly from winders or going through your Linux box attempting to print to it as a shared printer ??

If you're doing the latter, why ??  You should have no problem at all setting it up under winders as long as you understand anything about setting up network printers.

---

### Post by Black_Moon on 2010-01-08
This is network printer. (Connected to LAN, not to Local Machine).
Windows Machines can't see it without special tool utility. (CUPS can see).

So, Windows machines can use it only if it is shared printer. 
As I have Linux machine as office server (always working), 
so using shared printer is most suitable variant :KS

---

### Post by pricetech on 2010-01-08
Not to be argumentative but I just checked that model on HPs site and the driver is available with no special software required.

What version of winders are you using ??

---

### Post by Black_Moon on 2010-01-09
winXP & win2003

---

### Post by pricetech on 2010-01-11
Drivers for both of those versions of winders are there on the site.  Ne reason you should not be able to use the printer directly over the network.

---

