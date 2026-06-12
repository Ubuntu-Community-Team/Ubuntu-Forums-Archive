---
title: "Redirect website A to website B if server is down"
date: 2010-12-16
forum: General Help
---

### Post by duceduc on 2010-12-16
I am trying to figure out how I can redirect my websites to a webpage that stay, website is temporary down. 

I am running a home web server with couple of websites and am using zoneedit to monitor my dynamic ip changes. If zoneedit have issues or it is not updating the ip, how can I tell my server to redirect my xx websites to a webpage stating the sites is down for the moment?

---

### Post by efflandt on 2010-12-16
If you do not have DNS working or a stable site that can redirect to the proper site, you are up a creek without a paddle.

I am not familiar with zoneedit, but I have been using no-ip.com for nearly 10 years without any problems, until I suddenly noticed that they dropped their no-ip.com subdomains (although, they have others like no-ip.org, no-ip.info, etc.).  So I had to grab my subdomain names on a different domain (or they can do dynamic DNS for your own domain).

Instead of tickling their server periodically with their client to grab my IP, I run a Perl script as a daemon on a Linux box that runs 24/7 using Perl LWP module to monitor the DSL IP on my modem/router and only notify no-ip.com when that changes, and that works reliably.  My Perl script checks my IP every 5 minutes, and logs to syslog hourly or if my IP changes.  The Celeron 300 PC that runs on has an obsolete SuSE 8.2 that has run without rebooting since July 2006.

I actually have 3 subdomain names from no-ip.com to play around with name based virtual web hosting configuration years ago (and default worm trap logged separately by apache if no names match).

---

