---
title: "Vidalia configure"
date: 2011-08-15
forum: General Help
---

### Post by ltchronic302 on 2011-08-15
Hey guys, I'm running backtrack 5 and since it's ubuntu 10.4 I need some help with vidalia. I installed tor, polipo and the tor firefox button as per the instruction on tor ubuntu community page [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor) and everything works out great(I'm able to start tor and polipo, check that they are running and verify I'm connected to the tor network via the check page)...until I get to installing vidalia. When I do the apt-get install vidalia it starts installing then brings up a config page and says 

"Vidalia needs to communicate with the running tor daemon so that it can provide a gui for it. This requires either the manual reconfiguration of Tor to allow secure authentication (recommended) or a restart of Tor under Vidalia's control.

*No Configuration- leave tor running for now. Vidalia will not be able to communicate with Tor until it is manually reconfigured.
*One-off restart: stop Tor now so Vidalia can stat it, just this once - Tor will start by itself on reboots, so manual configuration will still be required.
*Permanent Takeover: stop Tor and simply let Vidalia handle starting it whenever you run Vidalia (not usable on a multi-user system)"

I'm guessing the best is to configure it manually but I have no idea how to do that after it's installed. Can someone help?

---

### Post by CrazyJones on 2011-11-25
[B]Try this

1.[/B] Add the Lucid repository in Maverick and install TOR, Privoxy and Vidalia (using the command terminal): 
echo "deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) experimental-lucid main" | sudo tee -a /etc/apt/sources.list 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 886DDD89

Then, along with TOR you may also want to install Vidalia (a GUI for  TOR) and Privoxy (non-caching web proxy with advanced filtering  capabilities): 

sudo apt-get update sudo apt-get install vidalia privoxy tor

[B]



2.[/B] This is optional - if you want to use TOR as a SOCKS5 proxy, also follow these steps:
Edit the Privoxy config file: sudo gedit /etc/privoxy/config

And paste this at the bottom of the file, then save it: 
Code <#> 
forward-socks5   /               127.0.0.1:9050.

Yes, there's a space and a dot at the end.




**3.** Restart TOR and Privoxy to complete the process:
Code <#>
sudo /etc/init.d/tor restart sudo /etc/init.d/privoxy restart

---

