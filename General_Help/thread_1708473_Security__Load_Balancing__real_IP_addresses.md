---
title: "Security / Load Balancing / real IP addresses"
date: 2011-03-16
forum: General Help
---

### Post by gzader on 2011-03-16
So I've set up a mini farm using heartbeat, haproxy and apache and I'm using SSL.

The problem is getting the real ip of the user coming to my site.

Regardless of SSL or not I only get the proxy's IP address. So for non-ssl we move to X-Forwarded-For in the header. I am concerned that it can be potentially spoofed and I have not found a definitive statement on this. I know that each proxy along the way adds their IP to end of the header and that the right most one is in theory the one HAProxy saw. I am only concerned with the right most one. 

The issue is that parts of the site are only visible from certain IP addresses. (I have password protected security in place as well.) The idea being that the less people who can get to the login / secured area, the less threats/noise I have to face.

But with XFF I can't be sure that the people talking to those pages are really from where they say they are. Or can I? 

The second part is SSL. I'm currently forcing a user to visit and insecure page so that I can read the XFF header (assuming that I can find a way to make this trusted) and then they can go into SSL. This in theory works but I think it means that as I set up the session in the open, someone can see the cookie being set up, wait a few minutes and then go into a known (password secured) page as if the user had authenticated as well.  I suppose the answer here is to set a second cookie with the user saying that the account has been secured and to differentiate from the non-ssl origination.

Any ideas or help here would be greatly appreciated.  Once I get all of this working I plan to write it up fully explaining everything needed to setup a small enterprise cluster with multiple virtual ips, balancing and ssl.

Thanks in advance!
G

---

### Post by gzader on 2011-03-17
So a small update:
If someone sends a spoofed X-Forwarded-For of  : 11.22.33.44 to HAProxy where the spoofers real ip is 192.168.11.22,  when HAProxy passes it on, it will show an XFF of 11.22.33.44,  192.168.11.22

I believe this to be correct. This means in theory that I'll have a correct method for limiting IP addresses.  

This also opens up using stunnel which will forward the SSL connecting address with an XFF header as well (if I have everything understood correctly).

This means I should have a reliable IP all the way through. This should also allow me to establish an initial session securely and avoid issues with stealing someone's session.

Another idea I had (which is more expensive in terms of IP addresses) was if I knew I was talking on wwwfarmserver1 it could generally be assumed that the box was up and running. I could have the user connect to that server directly which would allow me to obtain a non-proxy IP address. But the idea of using an extra IP per server is very unappealing.

If anyone sees that I have made a terrible mistake, please comment.

Thanks!

---

