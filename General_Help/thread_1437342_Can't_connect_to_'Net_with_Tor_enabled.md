---
title: "Can't connect to 'Net with Tor enabled"
date: 2010-03-23
forum: General Help
---

### Post by ETW Grumpy on 2010-03-23
I'm running Ubuntu 8.10 in a VMWare Workstation environment.
I'm running Firefox 3.0.3 with the Torbutton installed.
I can connect to the Internet with Tor disabled, but when I enable Tor, I get a network timeout for every site I go to. I had Polipo installed, but I purged it and have the browser set to connect directly to the Internet. I'm new at Linux, so I figure I've messed up a setting somewhere, or something similar. Anyone have any ideas?

---

### Post by cbraxton on 2010-03-23
> **ETW Grumpy said:**
> I'm running Ubuntu 8.10 in a VMWare Workstation environment.
I'm running Firefox 3.0.3 with the Torbutton installed.
I can connect to the Internet with Tor disabled, but when I enable Tor, I get a network timeout for every site I go to. I had Polipo installed, but I purged it and have the browser set to connect directly to the Internet. I'm new at Linux, so I figure I've messed up a setting somewhere, or something similar. Anyone have any ideas?

Do you have tor installed? Is it running and able to create a tor circuit?

Assuming tor is installed, enter the following from a terminal:

```

sudo /etc/init.d/tor start
sudo tail -f /var/log/tor/log

```

...and see if tor is initializing properly.

Are you connecting to tor through privoxy? Is that up and running and configured to connect through tor? Check that /etc/privoxy/config contains the following:

```

forward-socks4a / 127.0.0.1:9050 .

```

---

