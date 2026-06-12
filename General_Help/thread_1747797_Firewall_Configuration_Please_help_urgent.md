---
title: "Firewall Configuration Please help urgent"
date: 2011-05-03
forum: General Help
---

### Post by suresh_vandiyur on 2011-05-03
Hi All,

I need to block some unwanted websites. Any tool available for the ubuntu and then how to block website for one network. please help me.

Thank you,

Regards,
Suresh

---

### Post by rodeh on 2011-05-03
A quick fix would be to edit the 'hosts' file. This file acts as a local DNS table, if an url is listed in this file then the computer will use the associated IP address rather than send a request to a remote DNS server.

To do this open a terminal and

```
sudo gedit /etc/hosts
```this will open the file for editing.

Then all you need to do is use an IP address that will not direct to the outside world, such as the loopback address - 127.0.0.1

e.g if you felt the need to block ubuntu forums for salacious and frankly dodgy content you would add this (This however is not recommended ;)):

```
127.0.0.1 [www.ubuntuforums.org]("http://www.ubuntuforums.org/")
```A useful source of addresses that you may wish to block can be copy/pasted from here:
[http://winhelp2002.mvps.org/hosts.txt](http://winhelp2002.mvps.org/hosts.txt)

*One thing to note is that a very large hosts file (many entries) may slow down network performance, I use this method and don't really notice any impact.

Another option if you use Firefox is to use an addon such as Adblock Plus:
[https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/)

Subscriptions to blcoking lists can be found through this page:
[http://adblockplus.org/en/subscriptions](http://adblockplus.org/en/subscriptions)

---

### Post by suresh_vandiyur on 2011-05-03
> **rodeh said:**
> A quick fix would be to edit the 'hosts' file. This file acts as a local DNS table, if an url is listed in this file then the computer will use the associated IP address rather than send a request to a remote DNS server.

To do this open a terminal and

```
sudo gedit /etc/hosts
```this will open the file for editing.

Then all you need to do is use an IP address that will not direct to the outside world, such as the loopback address - 127.0.0.1

e.g if you felt the need to block ubuntu forums for salacious and frankly dodgy content you would add this (This however is not recommended ;)):

```
127.0.0.1 [www.ubuntuforums.org]("http://www.ubuntuforums.org/")
```A useful source of addresses that you may wish to block can be copy/pasted from here:
[http://winhelp2002.mvps.org/hosts.txt](http://winhelp2002.mvps.org/hosts.txt)

*One thing to note is that a very large hosts file (many entries) may slow down network performance, I use this method and don't really notice any impact.

Another option if you use Firefox is to use an addon such as Adblock Plus:
[https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/)

Subscriptions to blcoking lists can be found through this page:
[http://adblockplus.org/en/subscriptions](http://adblockplus.org/en/subscriptions)

That i need block my local network it around 50 to 60 members. i need to go to each every people hosts files add the sites.i need the tool for block the entire network. please help me

Thank you,

Regards,
Suresh

---

### Post by rodeh on 2011-05-03
Apologies, I read your post too quickly and skimmed over the network part. 

Let me get this right, you have a local network with 50 to 60 client pc's? Would it not be easier to edit the policies on the router (or hardware firewall, or local DNS server if you have either) to block outgoing requests to specific ip addresses than it would to individual clients?

---

