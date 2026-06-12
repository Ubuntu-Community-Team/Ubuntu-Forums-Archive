---
title: "ISA functionallity wanted..."
date: 2009-07-21
forum: General Help
---

### Post by arcanus on 2009-07-21
I know this is banned in the Linux world, but the company I work for desperatly need some functionallity that the MS ISA server provided.

We have recently thrown the ISA server out of the window (yay :D), and upgraded to a actual firewall from Cisco.

The only problem is that we have only one official IP, and multiple servers on the inside (Customer portals, heavy project management systems and other sorts of web applications).

The thing we had the damned (pardon my french) ISA server do, was to forward requests to webservers internally transparent to the user, who used our [http://example.com/](http://example.com/)[...] address (and ofc, port 80/443 is usually not blocked in a firewall and is thus always accessible).

Just to clarify;
[http://example.com/customer](http://example.com/customer)
  This would return the site from our customer server.
[https://example.com/subversion](https://example.com/subversion)
  This would return the subversion repo from our subversion server.
[https://example.com/project](https://example.com/project)
  This would return the web frontend for our project management system.

All the sites were querried from the outside, and then routed through our ISA server to the correct webserver.

Any help would be greatly apreciated! Don't tell me that the Microsoft Internet Security and (de)Acceleration Server does something that I can't do with a proper configured Linux server ](*,)

Magne

---

### Post by t4thfavor on 2009-07-21
I think it does, In the Linux world you only need one webserver, and apache does all of that. I have been looking for the same functionality, and have yet to find it.

So I started using IIS 6.0, with host header filters.

I know exactly what you want, I'm just sorry to say I think your sunk finding an exact replacement.

---

### Post by arcanus on 2009-07-21
> **t4thfavor said:**
> I think it does, In the Linux world you only need one webserver, and apache does all of that. I have been looking for the same functionality, and have yet to find it.

So I started using IIS 6.0, with host header filters.

I know exactly what you want, I'm just sorry to say I think your sunk finding an exact replacement.

Not quite the exciting news that I was hoping for :-(

Is there any way I can configure a named-virtual hosting for it then? Have apache proxy that stuff from a different server? The problem is that some of the stuff I need hosted runs on a tomcat AS on a different server, on port 8080... So I would need the apache server to forward requests for customer.example.com/ to customer.server:8080 and relay the information from there? That could also be worth a try...?

---

### Post by arcanus on 2009-07-22
Solved the problem, with more or less exactly what I wanted! \\:D/

The way I solved it, was to use the Apache server to act as a proxy server.

I configured two virtual hosts, one for http, and one for https. So far so good, these two got poked through the firewall to the server.

Then I activated the proxy module in apache, and reloaded the configuration files.

```
$ sudo a2enmod proxy && sudo /etc/init.d/apache2 force-reload
```

Then i added a proxy.conf file in the /etc/apache2/conf.d/ folder (which gets sourced automagically).

This file containes (for the sake of the OP):

```

# Deny proxy requests. Open relaying ANYTHING is bad...
ProxyRequests Off

# Allow this module to be used by anyone, anywhere.
<Proxy *>
  Order deny,allow
  Allow from all
</Proxy>

# Add the proxy to our customer server
ProxyPass /customer http://customer.server
# And back to the one requesting it
ProxyPassReverse /customer http://customer.server

# Add our project server
ProxyPass /project http://project.server
ProxyPassReverse /project http://project.server

```

Then reloaded the apache config files again
```
$ sudo /etc/init.d/apache2 force-reload
```

And voila! Any connection made to the server, will behave exactly like I want them too. The great thing about this, is that externally, every single web site we want to pass outwards, is accessible via HTTPS! This is becaus the TLS session is between the end user and the proxy computer, and via HTTP internally. This is GREAT!

I am marking the thread solved, and hoping that noone finds anything wrong with this setup :D

EDIT:
Well, I _WOULD_ mark the thread as solved if I could figure out HOW :D

Magne

---

