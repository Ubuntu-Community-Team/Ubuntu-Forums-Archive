---
title: "Software requirements for a new user"
date: 2010-10-08
forum: General Help
---

### Post by claydon on 2010-10-08
Hi all, 
 
Looking to switch my work laptop over to Ubuntu from windows 7 (or at least dual boot) 
 
I work as a Network Analyst and have a few pieces of software that I need to do my daily duties. I have had a look around but cannot find Linux alternatives to them. Hopeing that you can help 
 
GFi Langaurd - Mainly Used for locating PC's and the users logged onto them. Something similatr that allows me to sweep a range of addresses would be very useful.
 
mRemote - Allows you to build up a list of devices that you connect to via SSH/Telnet/RDP etc. Stores them in a tree structure.
 
Windows admin pack - DHCP/Active Directory access. Need to be able to change peoples passwords / reserve addresses etc. 
 
 
Ontop of these the majority of my time is spent in telnet (on cisco switches). Now terminal does that businees just fine but does anyone have any recomendation to making terminal work a little easy. 
 
We also have a MS exhange environment at work and I have sucessfully got a mail client on Ubuntu working fine with OWA. Is there any big drawbacks to doing this (such as meeting requests etc.) 
 
Thanks for your help in advance :)
 
 
EDIT:::
 
two more things sorry 
 
We use Cisco VPN client to remote in, would need something that allows me to do this and we have Belkin USB-Serial dongles for when we need to console into switches. I guess i would need some driver support for this when plugging into an ubuntu machine.

---

### Post by P4man on 2010-10-08
wow, reading all that, are you really sure you want to move to ubuntu lol?

Anyway, no expert but this might be worth a look as alternative to languard:
[http://www.nessus.org/products/](http://www.nessus.org/products/)
There might be free/oss products too, I dont know them.

For asset management, software center brings up "GLPI"
[http://www.ubuntugeek.com/glpi-it-and-asset-managemet-software.html](http://www.ubuntugeek.com/glpi-it-and-asset-managemet-software.html)
which looks rather basic
and Pads
[http://passive.sourceforge.net/](http://passive.sourceforge.net/)

Frankly, Id suggest you simply install ubuntu or boot the livecd and browse through the software center and see what you can use? Its one click install after all :)

If for some app you cant find a usable (and affordable) alternative, there is a fair chance these kinds of apps will run under wine.

As for connecting to exchange.. yeah its a pain. If you can convince the server admins, there are some connectors you can install on the server like Brutus:
[http://linux.softpedia.com/get/Communications/Email/Brutus-evolution-brutus-20729.shtml](http://linux.softpedia.com/get/Communications/Email/Brutus-evolution-brutus-20729.shtml)

If thats not an option, and you cant convince MS to open up their API's, then honestly, the next best solution is using a browser or running Outlook on wine or crossover :(

No idea about the VPN or dongles. I would expect these to work under linux, but worst case scenario, you can install windows in a VM and they can access the USB device if you install virtualbox PEUL version. Just saying since wine doesnt support access to USB.

---

### Post by CoolJohnB on 2010-10-08
You could also try these sites:

[http://en.wikipedia.org/wiki/List_of_free_and_open_source_software_packages](http://en.wikipedia.org/wiki/List_of_free_and_open_source_software_packages)

[http://www.linuxalt.com/](http://www.linuxalt.com/)

---

### Post by CoolJohnB on 2010-10-08
You could also try these sites:

[http://en.wikipedia.org/wiki/List_of_free_and_open_source_software_packages](http://en.wikipedia.org/wiki/List_of_free_and_open_source_software_packages)

[http://www.linuxalt.com/](http://www.linuxalt.com/)

Not sure how this got posted twice, sorry

---

### Post by claydon on 2010-10-08
Thanks for the links I will look into these. I have linux on a desktop at work and I have been installing software looking for similar products I need to use but I have never been entirely happy with what I have found. 
 
I can use my desktop for 80% of my work but it's the other 20% that stops me from making the swap permanent. Unfortunately something like not having VPN to connect outside of work is a real show stopper for me as I'm oncall.

---

### Post by KeyserSoze93 on 2010-10-08
For finding services running on the lan, you should try nmap.

---

### Post by HermanAB on 2010-10-08
Howdy,

You should install VMware Player and make a Windows 2003 Server VM.  It runs very well in a VM and then you can have all your old tools at the ready.

---

### Post by P4man on 2010-10-08
At the the risk of getting off topic, I recently came across this tool to migrate an existing (windows) install to a VM with just a click:

[http://blog.paragon-software.com/?p=439](http://blog.paragon-software.com/?p=439)

Works with VMware and virtualbox. Ideal if you are migrating to ubuntu and want to keep your old windows setup at hand without having to dualboot or having to reinstall it all.

---

### Post by jmszr on 2010-10-08
claydon,

Here are some links for VPN: [http://ubuntuforums.org/showthread.php?t=1495485](http://ubuntuforums.org/showthread.php?t=1495485) , [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN) , and, while this is for 9.04, it may be useful: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1227209](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1227209) .

Hope that helps.

---

