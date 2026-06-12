---
title: "Changing network (WIFI)"
date: 2006-04-06
forum: General Help
---

### Post by QwUo173Hy on 2006-04-06
When my computer boots up, it will only connect to the ESSID 'startrek' in the house I live in. If I rename the router or boot near some other access point, the laptop wont connect. Is there a way to get this to work?

Also, kwifimanager doesnt successfully change network either. Do I have to hard code in an ESSID somewhere and reboot every time?

Thanks in advance for any advice,
jarlath

---

### Post by ssalman on 2006-04-06
have you tried using 'any' as your ESSID? this will look for any AP near by and attach to it.

---

### Post by BlueNoteMKVI on 2006-04-06
Look into a package called "whereami" - I use it to manage the connections on my laptop.  You can do lots of great stuff with it.  For example, my laptop configuration does this:

-if there's an available lan connection (a cable plugged in) try to use it
--if I'm plugged in to my shop network, set the static IP I need for the shop and mount the samba shares on the other shop computers
--if I'm not in the shop, use DHCP for an IP address
-if there's no lan connection, load the wifi card driver
--if I'm at home, connect to the home wifi network and mount the samba share on the home server
--if I'm not at home, use dhcp to get an address

It took a lot of tweaking to make all that work, but it's all automatic - whenever I boot up the laptop at home, work or school it's set up correctly.  99% of the time in other places with wifi it works automatically.

---

### Post by ssalman on 2006-04-07
BlueNoteMKVI,

  could you please post your script, I'm intrested in setting up something similar? Thanks.

---

