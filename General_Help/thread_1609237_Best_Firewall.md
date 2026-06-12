---
title: "Best Firewall"
date: 2010-10-30
forum: General Help
---

### Post by newperson on 2010-10-30
I am currently using Firestarter and it seems to work great. The only problem I have is I set it to load on startup but it requires a password to start, so when you turn the computer on it asks permission to load Firestarter.

I suppose this is good as I am always aware that it is on, but what other firewall programs run on startup without having to be authenticated, that are good?

Thanks. 

I don't know how I am going to pass an IT course when I know nothing about computers!:confused:

---

### Post by coffeecat on 2010-10-30
Let's get one thing straight: firestarter is not a firewall. The firewall in Linux is the kernel iptables which is running all the time. The default settings in Ubuntu are just fine for most uses. Firestarter is merely a GUI configurator for setting firewall rules to be used by iptables, so it only needs to be run when you need to do some configuration.

I think you are getting muddled by Windows ways of working, using things such as zone alarm. You are in a different environment.

Next thing to say is that although firestarter has a nice user interface, it is not reliable. It is a dead, unmaintained project and has some decidedly unfortunate bugs.

If you really need a gui firewall configurator, I suggest you try Ubuntu's own gufw. It's in the repositories. But uninstall firestarter and every trace of what you did to get it running on startup first.

---

### Post by Rubi1200 on 2010-10-30
+1 to everything mentioned by coffeecat. 

Please do not use Firestarter!

For more about firewalls on Ubuntu:
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/IptablesHowTo?action=show&redirect=Iptables](https://help.ubuntu.com/community/IptablesHowTo?action=show&redirect=Iptables)
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by Soul-Sing on 2010-10-30
> The firewall in Linux is the kernel iptables which is running all the time.

No.

---

### Post by matt_symes on 2010-10-30
Hi

>  	Quote:
 	 	 		 			 				The firewall in Linux is the kernel iptables which is running all the time. 			 		 	 	 
No.
 		                   		  		  		 		 			 				

Leoquant could you clarify please. No is short and sweet but does not help the OP

Kind regards

---

### Post by Soul-Sing on 2010-10-30
> **matt_symes said:**
> Hi



Leoquant could you clarify please. No is short and sweet but does not help the OP

Kind regards

Indeed iptables, netfilter actually, is the embedded firwall in the linux kernel but not enabled and running by default.
With ufw/gufw you could enable [COLOR="Red"]and [/COLOR]configure netfilter. Firestarter isn't an option imo, because it is not maintained for several years now.

---

