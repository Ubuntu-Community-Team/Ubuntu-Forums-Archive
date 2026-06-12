---
title: "IPv4 Static IP settings, Cannot click apply!!"
date: 2011-03-04
forum: General Help
---

### Post by ubila on 2011-03-04
Hi all,
Im trying to setup a static IP address, but the apply button is greyed out and unclickable! 

Edit: 
Using Ubuntu 10.10 Desktop

I go into System > Preferences > Network Connection
Then IPv4 Settings,

Manual

Address: 192.168.2.2
Netmask: 255.255.255.0
Gateway: 192.168.2.1

DNS Servers: 60.234.1.1, 60.234.2.2 

Thats all the info ive added. I clicked Add button after entering IP information.

It seems all filled out, but the Apply button wont let me click it!!

Whats going on! :(

When i hover over the Apply button it says "Authenticate to save these settings for all users"

Thanks!

---

### Post by pqwoerituytrueiwoq on 2011-03-04
are you sure you clicked off of the gateway blank
also be sure that is what you typed

---

### Post by ubila on 2011-03-04
> **pqwoerituytrueiwoq said:**
> are you sure you clicked off of the gateway blank
also be sure that is what you typed

Yes i have since clicked elsewhere and hit the add button, still wont allow me to Apply. Could this be a permissions issue? I dont know how to run it as admin outside of terminal!

---

### Post by pqwoerituytrueiwoq on 2011-03-04
if the edit button has a key icon instead of a pencil in it you need root access in which case it will ask for a password
i just tried to add those settings as soon as i had the net mask in the apply button lit up i also had address in

---

### Post by billmiller3 on 2011-04-22
I ran into the same issue in ubuntu 10.10
I was not able to manually add a static Ip address to Eth0 using the network connections tool 
The apply button was grayed out.

To Resolve it:
During boot I went into the BIOS under integrated peripherals.
Inside Integrated Peripherals I had to enable "Lan Options Rom"
It was with all the rest of the controllers settings in BIOS.

Hope this helps someone out...

---

