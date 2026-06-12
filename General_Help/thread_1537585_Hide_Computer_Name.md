---
title: "Hide Computer Name"
date: 2010-07-23
forum: General Help
---

### Post by Seeked on 2010-07-23
How would one hide the name of my computer on Ubuntu 10.04?

For example, when I view the DHCP client list on my router I can see the name of my computer.  I would prefer to hide that so only the IP address would be available on the network.  Or when I ssh into a shell and run who you can see my computer name.

Thank you in advance.

---

### Post by Seeked on 2010-07-23
Bump

---

### Post by CharlesA on 2010-07-23
It's not possible to do that as far as I know. It will always broadcast the hostname when asking for an ipaddress from DHCP.

I think you can edit the prompt to not show the hostname, but why bother?

---

### Post by Seeked on 2010-07-23
Because its identifiable information that I may not want others to see.

---

### Post by Zeike on 2010-07-23
Your hostname probably isn't any more identifying than an IP address.

You can't stop your hostname from being broadcast, thats the whole point of a hostname.

You can change it however. I'm pretty sure all you have to do is edit /etc/hostname as root, and reboot.

---

### Post by CharlesA on 2010-07-23
Unless your hostname is something like "bobspc" then how is is exactly is it identifiable information?

If you change the hostname in /etc/hostname don't forget to edit the /etc/hosts file and add the new hostname, otherwise you will get errors when trying to use sudo.

---

### Post by AggravatedGestalt on 2010-12-21
This seems a worthy goal. Is there really no other way to accomplish this?

---

### Post by ManyBeers on 2010-12-21
I have the opposite problem and would like my laptops hostname to display.
It currently shows as"unknown".
What files do I need to edit to achieve this end?

---

### Post by AggravatedGestalt on 2010-12-28
In the router's general settings I also show as UNKNOWN, but not in the DHCP section; there my host name is shown. 

I also use wicd (saw your post on another thread), so maybe that is the reason.

---

