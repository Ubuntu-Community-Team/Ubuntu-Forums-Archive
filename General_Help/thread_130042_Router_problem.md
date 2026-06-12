---
title: "Router problem?"
date: 2006-02-15
forum: General Help
---

### Post by Geir Smestad on 2006-02-15
I have a problem with my internet connection. I have an ADSL line shared with two Windows computers (one 98, one XP) through a standard hardware router. The network works fine on both Windows computers, but I am unable to access the net on my Ubuntu box. I am able to ping web sites from the console, but when I try to load a page in Firefox, it halts on the message "waiting for (url)". When I enter the router IP address, I am asked for the login and password, but this is as far as I get in accessing the router software.

Any suggestions?

---

### Post by Ramses de Norre on 2006-02-15
Have you got your DNS servers configured? Looks like you have the wrong one's.
Can you open your router page? you might try the DNS servers listed there, otherwise check the info from your internet provider on which to use. 
You can configure them with system<administration<networking.
They are used to get the IP for a given url, that's why you can ping but you can't open url's.

---

### Post by Iowan on 2006-02-15
Gateway settings?

---

### Post by steve.horsley on 2006-02-15
When you say you can ping web sites from the console, is this by name or by IP address? If you can ping by name (e.g. [www.ubuntuforums.org](www.ubuntuforums.org)) then it's difficult to think what's wrong with firefox. It may be interesting to try firefox with the IP address rather than the name, e.g. [http://64.21.33.9/](http://64.21.33.9/). Also, check that firefox isn't configured to use a proxy.

---

### Post by Geir Smestad on 2006-02-15
Sorry about not being specific enough. I am able to ping an url and the DNS servers are correct. HTTPing an IP address gives the same results as HTTPing an url. As for the gateway, I take it that you mean telling the ethernet interface the router's address? Choosing 'static IP address' and assigning a local IP address for the computer (192.168.1.3), the network's subnet mask (255.255.255.0) and the router's internal address (192.168.1.1) in 'Network Interfaces' gives no results.

For the record, Firefox is able to download the small icon that appears in the upper left corner of a tab when I enter an url.

[Note: In addittion to the network router, I also have an ADSL modem/router with an internal IP address of 10.0.0.1. Does this thing complicate the matter?]

---

### Post by nanotube on 2006-02-15
seems like some kind of problem with firefox. just to make sure, try another browser?
(eg, elinks - text mode browser)
or just open up a terminal, and "telnet google.com 80" and see if you can connect and get some stuff.

---

### Post by Geir Smestad on 2006-02-16
Indeed, elinks works. Guess I'll hit the Firefox forums then. Thanks.

---

### Post by soonindallas on 2006-02-16
Try disabling IPv6 support in firefox.  It's enabled by default and gives problems unless you're using IPv6, which I doubt...

in firefox, enter "about:config" in the location bar.

in the filter bar type "ipv6"

you should see an attribute "network.dns.disableIPv6": you want the value to be true for IPv6 to be disabled.

if the value of the attribute is "false", double-click it to toggle to "true"

you might need to quit and restart.

post back on your progress.

---

