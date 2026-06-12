---
title: "Can't print! - System&gt;Admin&gt;Printing unable to contact CUPS server"
date: 2006-04-10
forum: General Help
---

### Post by snufkin on 2006-04-10
Hi - I've been struggling with this one for a few weeks now, but I **really** need to resolve it.  I run my own small business using only Ubuntu (5.10), and rather need to print some invoices if I am to get paid! :( 

Here's the problem.  Printing was working fine untill a few weeks ago, when my LaserJet 4l suddenly became unavailable.  When I tried to set it up again using the 'System>Admin>Printing' tool, I got the error message:

"The CUPS server could not be contacted"

... and the gnome-cups-manager tools has been unavailable since.  Also, my browser times out when looking for [http://localhost:631/](http://localhost:631/) to I can't probe that for answers.

I've tried starting, stopping and restarting cups with ```
sudo /etc/init.d/cupsys [stop|start|restart]
``` and it **seems** that cups is working ok (I get "* Starting Common Unix Printing System: cupsd [ ok ]").

I've also searched these forums, and tried most things from Weman's "[The CUPS server could not be contacted]("http://ubuntuforums.org/showthread.php?t=105423")" thread...
* checked my loopback eth interface is up (it is)
* tried kenweill's suggestion of starting/stopping the cups service and rebooting (didn't work)
* Added 'ServerName localhost' to /etc/cups/client.conf, then restarting cupsys (doesn't have any effect for me)

Finally, I've just got all the latest package upgrades for Breezy using Synaptic, and cups/footmatic-filters are all the latest available versions.  Still no improvement tho...

I hope someone can help.  I get the feeling that reinstalling Breezy but refusing updates would work, and I know I can print using the Live CD - but I'd really rather solve this properly.

Thanks, in anticipation...

---

