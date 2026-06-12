---
title: "Firefox hangs and won't connect"
date: 2006-03-26
forum: General Help
---

### Post by frostie on 2006-03-26
I've installed 5.10 on a friends computer but have not so far managed to get Firefox to connect to the internet. It just hangs on waiting for [www.google.co.uk](www.google.co.uk).

eth0 is connected to a router at 198.168.1.1 on dhcp and I can ping any web site I like with total success. /etc/resov.conf shows the router address as a nameserver. I tried the ipv6 toggle but to no avail.

Two other computers running ubuntu on the same router have no problems whatsoever and the set up in the networking dialogue exactly mirrors the dhcp set up on the other two working computers. I've rebooted the modem any number of times and the router also. (I can only reboot the router from another box though, this one just gives me a login prompt and then 'the document contains no data' box).

I'm at a loss as to know what to do now. I have reinstalled twice (and installed Mandriva in between which had no problem at all, firefox ran fine from there).

Does anyone have any suggestions what to try next?

---

### Post by frostie on 2006-03-26
I've run out of time now really, I just thought if someone had a quick solution I could get through it. I'm installing Debian as I need to get it back to him in the morning. It seems to have configured things nicely during the installation anyway so I'll take it from here. Shame though.

---

### Post by moephan on 2006-03-26
Could it be IPv6 issues?

Try this:

1. Open firefox and type &#8220;about:config&#8221; in the address box.
2. Search for "IPv6" and then set network.dns.disableIPv6 to true.

HTH

Cheers, Rick

---

### Post by Kevinator on 2006-03-26
Did you try any site other than google.co.uk? I would obviously try other sites, then I would try pinging a few sites (as you apparently did) and verify that DNS is working. Assuming DNS is working (i.e., ping resolves the name to an IP address), I'd next verify that I can connect to port 80 on the server, probably with this:

nc -vvv [www.google.co.uk](www.google.co.uk) 80

though people commonly use telnet for this purpose as well. Assuming that connects, I would try to fetch the index page by typing

GET / HTTP/1.0

followed by two carriage returns. If the response is 200, then that would suggest that the connection is fine and the server is responding properly, therefore the client (firefox) is the problem. In that case, I'd probably try presenting the issue on the Mozillazine forums. (The first suggestion I'd give if you were asking there would be to nuke the firefox profile and trying again.)

---

### Post by frostie on 2006-03-26
Ok, thanks for the suggestions. I decided I gave up too easy so I'm just waiting while it reinstalls.

I did try the IPv6 toggle to no avail I'm afraid and I was able to ping google and the BBC which were the two I tried.

When this installation has completed I'll see where I am and try the other suggestions...thank you.

regards,

---

