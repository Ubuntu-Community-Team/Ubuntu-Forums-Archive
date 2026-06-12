---
title: "SNORT on only one interface?"
date: 2010-06-22
forum: General Help
---

### Post by J-Rod on 2010-06-22
I have installed snort from the repository, and installed acidbase and have it all working and functional. Currently this IDS is sitting behind an ASA firewall, with the listening NIC in PROMISC mode, connected to a spanned port on the ASA. The other main NIC is connected to the internal network, for remote administration and other monitoring. Snort is generating lots of "alerts" on the internal network that I really don't care to see at this point in time.

Where do I go to ensure Snort is only active on the listening interface? I poked around in the /etc/init.d/snort and snort.conf, but I am not sure exactly where to look. Would I have to just change HOME_NET to match the IP range of the interface I am listening on? I mean the traffic I want to see is any outside traffic to the website that is behind the firewall. I was hoping there was just a way to start snort with a flag that only enables listening on the interface I choose. Any help is greatly appreciated!

---

### Post by J-Rod on 2010-06-22
Well I think I found what I need is actually to create a new "sensor" maybe? Looking in the acidBASE pages, I see there's only one configured in /acidbase/base_stat_sensor.php, and it's bound to my internal interface. I'll dig through the snort pages and see if I can find anything, in the meantime if anyone can chime in I'll be watching! :)

#edit#

> What I did, using BASE, is to start two instances of snort and only vary the "-i " parameter on the command line, and used the same snort.conf for each. Neither the sensor ID nor the the interface is mentioned anywhere in snort.conf. New sensor IDs are automatically generated, and BASE can distinguish between them just fine. Only one database is needed, and only one BASE instance is needed. All the alerts will be displayed intermixed, which is just fine with me. The details show which sensor, source and dest IP, etc, are involved. Of course, if you really want to separate them using separate databases you can.

I found this while trawling the intarwebz. It looks like since I only need the one interface listening, I simply need to find out where to edit the startup options that were created when I installed from the repository. Other tutorials have me setting up from source, but I'd like to stay with packages since it makes upgrading in the future less hassle.

---

