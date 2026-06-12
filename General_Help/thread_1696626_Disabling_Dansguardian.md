---
title: "Disabling Dansguardian"
date: 2011-02-27
forum: General Help
---

### Post by Myfathersheart on 2011-02-27
I am trying to disable dansguardian, but 

/etc/init.d/dansguardian stop 

is not working. Can anyone help please?

---

### Post by abecrab on 2011-03-05
That alone isn't likely to do it.

This depends on whether you've set it up to be a "transparent proxy", or instead expect to configure web browsers to connect to a proxy.

For a transparent proxy you'd configure the firewall to redirect all traffic to port 80 (http) to the port that dansguardian is listening on.  dg then connects to a proxy, typically squid, listening on a different port, probably 3281.

For web browsers configured to connect to a proxy, the browsers point to the port dg listens on, probably 8080.  Dg then connects to a proxy, typically squid, which connects to the internet.

Thus if you're going to stop dg, how will web traffic get to the web?

In the former case you have to reconfigure the firewall not to redirect http to the dg port - take that rule out so http traffic goes to the web.

In the latter case you might reconfigure the port the proxy listens on to be 8080 because dg is no longer interposed.

Another thing you could do if what you want is for just yourself not to be filtered but for others to continue filtered is to change the transparent proxy rule in the firewall so that packets are not forwarded for you user (as well as the user the transparent proxy runs as.)  This applies only to you browsing on the machine dg is on.

Hope that helps -

Abe

---

