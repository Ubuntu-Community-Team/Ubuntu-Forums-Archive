---
title: "Cisco VPN?"
date: 2010-05-21
forum: General Help
---

### Post by m00nshine on 2010-05-21
Hi,

I go to system > preferences > network connections in 9.10 and import a profile. The vpn seems to connect but I cannot ping computers on the remote network. When I attempt to ping, it seems it can see an ip (DNS must be working) but I can't actually ping the machine or rdp in. I've disabled my firewall and rebooted and that didn't help. What can I do? 

:confused:

---

### Post by hnarwan on 2010-05-30
I'm having a pain in my *** working this out. Replying to bump this question up and hopefully get an answer.

I've used both the standard vpn option under the network configuration tool and also KVPNC, not sure if you had any issues with opening internet pages with the standard vpn client under System>Preferences>Network Connections (or the icon in the tasbar) but I did. KVPNC gets around that (with the default installation options). I didnt need to tweak anything.

But now i'm stuck where you are, I've used both Terminal Server Client and Remote desktop viewer, tried just the machine name and the FQDN but I cant even see my machines on my network or ping them.

This problem is very annoying, i'm sure there's a bunch of people with this setup working ok but not sure what we need to do to join that group.

---

### Post by hnarwan on 2010-05-30
m00nshine have you tried using Terminal Server client and specifying the IP address instead of the machine name?

I assume you can ping the machine from the terminal? For some reason i cant us the machine name (either in a ping or terminal server client connection) but when I use the ip address in both i'm good. It's a little annoying, i'd prefer to use the machine name as i'm accessing so many machines at work but hey at least it's working.

Not sure if this is going to help you, let me know how you get on.

Hardeep

---

### Post by m00nshine on 2010-06-10
Well, actually, I reinstalled 9.10 and now all of the VPN options are grayed out. I haven't taken any steps to work on this recently. There was a site I found during a google search that detailed the steps to get the buttons back. If I do get the vpn working again, I will attempt to use the ip. Thanks.

---

