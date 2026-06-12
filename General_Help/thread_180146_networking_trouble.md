---
title: "networking trouble"
date: 2006-05-21
forum: General Help
---

### Post by Dazed_n_Confused on 2006-05-21
Let me first say that I've had copies of ubuntu for several months, but have only recently used it. I didn't even know about chmod untill a few weeks ago :p Though, I had help from people on another comunity with vim and general command-line file browsing. Case in point, I'm not a compleat n00b, but I'm not far from it.

As for my problem...
I can access shared hard drives, but I can't connect to the internet via my shared modem.

I first used the windows xp networking wizard to configure my windows machine. WinXP by default tries to give my PC a static IP - since my network supports DHCP, I clicked the other radio button to make it use DHCP. If I don't do that step, then I can't access my shared hard drives and modem sharing still doesn't work. Then I run through the ubuntu instalation and let it automaticaly configure things on that end. 

WinXP at least _thinks_ my modem is shared, becuase it says so under the modem's status. I've been toying with various firewall settings (and even compleatly disabling the firewall), and since I can at least access shared hard drives the network must be configured right.

What am I missing?

P.S. If anyone could tell me a way of running *only* the network configuration portion of the ubuntu instalation, please do. The graphical networking tool under system->administration doesn't seem to save the settings.

---

### Post by Koori23 on 2006-05-21
When you say Modem.. Do you mean Dial-up 56k modem or broadband Cable modem? This might be part of the issue. I'm afraid to say but Ubuntu isn't the greatest with regular dial-up modems. Windows also doesn't like to share ANYTHING, so relying on WinXP mentioning that it won't share with another OS isn't suprising.

If you could please elaborate on whether or not it's a dial up modem, we can dig further into this.

Forgive me ahead of time if that is a stupid question but it just sounds like we're talking about dial up.

---

### Post by Dazed_n_Confused on 2006-05-21
Yes, it is a dialup modem.

To explain a little better...
I have an hsp56 PCI modem installed in the windows box. In the XP network wizard, I select the radio button that says something like "This computer connects directly to the internet, other computers on my network connect through this one" (same as the last time I had things working right). I then gave the machine a network name of "WIN" and a workgroup of "MSHOME". Durring the ubuntu instalation, I give my ubuntu machine the host name "ubuntu" and it won't present me an option to set the workgroup unless I change the debconf setting to "low" - the times that I have gone that rout, I give the ubuntu box a domain of "MSHOME". It doesn't seem to mater wether I specify the workgroup here though, I guess it defaults to mshome.

Back in december, with ubuntu 5.04, I managed to get the shared modem setup to work beutifuly. Then I tried to add a labtop to the network and everything broke. Lately I've had renewed intrest in linux and decided to try out ubuntu 5.10.

If I were more network savy, I could maybe set it up to work like a proxy or something. Messing with IPs and ports is over my head though, I don't understand all the lingo.

---

### Post by Dazed_n_Confused on 2006-05-24
In case someone else happens to be searching these forums for solutions to the same problem....

I talked to someone in IRC today who informed me that windows will try to act as a DHCP server, which apparently conflicted with my router's own DHCP capabilities.

Disableing DHCP on my router fixed the problem. 

To configure your router, use a web browser to connect to it. Type the IP of your router in the address bar - where you would normaly type [www.whatever.com](www.whatever.com) (for my belkin router, the default IP was 192.168.2.1 but I gather that different manufactures use different default values). First you might have to un-share your modem and/or disconect other PCs from the router depending on how bungled things have gotten :)

---

