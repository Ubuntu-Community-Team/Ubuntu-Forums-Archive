---
title: "web server problem"
date: 2010-05-19
forum: General Help
---

### Post by evaristegalois on 2010-05-19
I want to set up moodle and need to give my computer some capability to act as a server. I am following the steps at

[http://docs.moodle.org/en/Step-by-step_Install_Guide_for_Ubuntu](http://docs.moodle.org/en/Step-by-step_Install_Guide_for_Ubuntu)

although my question is not really related to moodle. Here is the problem: setting everything up to make my computer accessible from outside has worked so far. I got myself a static IP address using a dynamic dns server and can ssh into my computer from any other computer connected to the www. So,

ssh -l myname 192.168.0.150

works on my local computer just as

ssh -l myname myname.homelinux.org

works on any computer on the web.

But,

[http://192.168.0.150](http://192.168.0.150) (local)

tells me that everything is working while

[http://myname.homelinux.org](http://myname.homelinux.org) (anywhere)

doesn't go through (connection times out).

I am using LAMP (apache) for all of this, but I don't know anything about it.

Please advise. Thank you!

---

### Post by evaristegalois on 2010-05-19
I should add that on DynDNS.com, I selected both ssh and web page where they ask

What do you want to use this host for?

Select services and devices you would like to use with this hostname.

---

### Post by evaristegalois on 2010-05-20
It's not a dyndns problem. If I find out my IP address and try that it doesn't work either:

[http://96.49.75.14](http://96.49.75.14) (my temporary IP address) doesn't work
[http://192.168.0.150](http://192.168.0.150) works (locally), showing me the index page at /var/www

Could it be the router? But port 80 and 443 are open. I checked in the router's settings.

---

### Post by evaristegalois on 2010-05-23
Problem solved: I didn't turn on "Remote Management" on my router. Sorry about that, but I honestly didn't see that anywhere in any of the setup guides. Thanks everybody!

---

