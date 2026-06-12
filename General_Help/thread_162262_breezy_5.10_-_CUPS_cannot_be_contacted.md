---
title: "breezy 5.10 - CUPS cannot be contacted"
date: 2006-04-18
forum: General Help
---

### Post by gbh on 2006-04-18
I had to resort to a new post after hours of searching on these forums for my print setup problem (and lots of googling)

I installed Breezy Badger 5.10 - my very first Linux installation.  Everything went smoothly but I am unable to configure my printer.

Access to "System Settings->Printers" always hangs for a long time and finally fails with  "The CUPS server could not be contacted..."

CUPS Server Settings indicates that host is "localhost" and port is 631. User is the logon user and password is blank.

I have tried "/etc/init.d/cupsys restart" and get the response:
"* Restarting Common Unix Printing System: cupsd [ ok ]"

ps -Al | grep cupsd 
indicates that cupsd is indeed running.

I also restalled CUPS, but still the same error.

I cannot access the web interface "http://localhost:631" - this too fails with a timeout.

Any help is highly appreciated.

---

### Post by peterand on 2006-04-19
Hi,

I have had exactly this problem recently.
The cause for this in my case was that the loopback device wasn't configured.
Can you ping localhost (127.0.0.1) ? 
If not, that would probably be a good place to start!

Cheers

---

### Post by gbh on 2006-04-19
Thanks a lot! That helped.

ping localhost was not working.  I tried:
**sudo ifdown lo**

But, it returned with the following error:
[COLOR="Red"]/etc/network/interfaces:22: too few parameters for iface line[/COLOR]

My /etc/network interfaces looks like this:
--------------------------
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0

iface wlan0 inet dhcp
wireless-essid MYSSID
wireless-key xxxxxxx

auto wlan0

iface eth0 inet [COLOR="Red"]dhcp[/COLOR]
---------------------------
The culprit was the last line - the entry in red was missing.

I added this and then:

**sudo ifdown lo**
**sudo ifup lo**

got the loopback running.

Now I have to figure out how to add my printer (a cheap Lexmark z34) using CUPS.  I downloaded the driver from their website, but CUPS does not seem to recognize it.

Thanks once again.

---

