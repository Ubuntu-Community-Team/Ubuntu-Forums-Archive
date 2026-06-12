---
title: "How do I set up SSL for several sites on the same server?"
date: 2010-07-13
forum: General Help
---

### Post by PaulWhipp on 2010-07-13
Server version: 9.10 fully updated, using Apache2.

I've been running an Ubuntu server on the amazon cloud for approaching a year now and various friends and clients have sites running on it - I set it up as a test and I never intended to end up administering a server but such is life:

Now I am being asked for SSL. The server has a single elastic IP and the domains are all set up as specific sites in /etc/apache/sites-available.

Is there any way that I can set up certificates for specific domains on the server?

I can see how I could do it for one site/one server. I have SSL enabled and working for the server itself but the ssl 'site' I set up just uses a single certificate and directs the requests to one folder. To use this approach I'd have to give each site its own server which would be cost prohibitive.

---

