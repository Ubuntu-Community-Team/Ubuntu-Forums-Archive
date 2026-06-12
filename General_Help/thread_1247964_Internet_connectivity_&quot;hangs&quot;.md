---
title: "Internet connectivity &quot;hangs&quot;"
date: 2009-08-23
forum: General Help
---

### Post by tomreid on 2009-08-23
Hi All,

I'm using Ubuntu 9.04 on a new HP Pavilion  system. I connect to the Internet on this system via wifi.

I'm having what I can only describe as a periodic "hang" of internet connectivity. I get no error messages, all looks fine, but I click on a web page, click on a link, Firefox will hesitate for around 20 seconds and then show me the contents of the link etc.

I see similar "hanging" behavior when I'm downloading podcasts or using the bit torrent client, i.e.  nothing will seem to be happening for around 20-30 seconds, the download will resume fine, it will hang, then resume again, and this cycle goes on. 

I have tried elimimating the obvious, I use two Macs running OSX on wifi on the same network and they don't show this behavior. I have dual booted this HP desktop with Vista and Vista does not do this, so I don't think this is a hardware issue.

That leaves me with a possible issue with the Linux driver for the Wireless G Lan card than came with the machine. This seemed to work out of the box when I installed 9.04, so I have not done any work on the driver.

Can anyone help me understand - could this be a driver issue? If so, how do I check what driver is running with the wireless card and how could I substitute another?

cheers

---

### Post by tomreid on 2009-11-13
After having no joy with resolving the I finally found the answer:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

specifically:

[COLOR=#cc0000][SIZE=4]ipv6[/SIZE][/COLOR]

Network became slow due to the unsupported ipv6 protocol, so disabling ipv6 could help. 

To disable ipv6 on Firefox Preferences, set the *network.dns.disableIPv6* to **true**.

   1. Type *about:config* in the address bar, press Enter.
   2. Find *network.dns.disableIPv6* in the list.
   3. Right-click -> Toggle.
   4. Restart your Mozilla application and try again.

---

### Post by tomreid on 2009-11-13
**Re: Internet connectivity "hangs"** 			
 			 			 		   		 		 		After having no joy with resolving the I finally found the answer:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

specifically:

[COLOR=#cc0000][SIZE=4]ipv6[/SIZE][/COLOR]

Network became slow due to the unsupported ipv6 protocol, so disabling ipv6 could help. 

To disable ipv6 on Firefox Preferences, set the *network.dns.disableIPv6* to **true**.

   1. Type *about:config* in the address bar, press Enter.
   2. Find *network.dns.disableIPv6* in the list.
   3. Right-click -> Toggle.
   4. Restart your Mozilla application and try again.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8308454") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8308454") 		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8308454") 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8308454") 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quickreply.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8308454") 		 		 		 		 		 			 		 		 		 	       	 	 		tomreid 	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=838942") 	 	 		[Send a private message to tomreid]("http://ubuntuforums.org/private.php?do=newpm&u=838942") 	 	 	 	 		[Find More Posts by tomreid]("http://ubuntuforums.org/search.php?do=finduser&u=838942") 	 	 	[Add tomreid to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=838942")

---

