---
title: "Problem with build-essential"
date: 2011-11-21
forum: General Help
---

### Post by Alphamonkey on 2011-11-21
**** 			 			 		   		 		 		[LEFT]Hi, while using a program I got this message:

"ERROR: Neither the sysfs interface links nor the iw command is available.
Please download and install iw from
http://wireless.kernel.org/download/iw/iw-0.9.22.tar.bz2"

I downloaded it and tried to "make" the file. This displayed the message.

Makefile:39: *** Cannot find development files for any supported version of libnl.  Stop.

after that I did "sudo apt-get install build-essential"

this returned

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

anyone know what I need to do to "make" files?

also I am looking for a decent and easy to use c++ compiler to use with ubuntu. 

Thanks.

Also I posted a similar post yesterday but realized it was under the wrong section so sorry about that.
[/LEFT]

 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11472272") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11472272")

---

### Post by snowpine on 2011-11-21
> **Alphamonkey said:**
> Makefile:39: *** Cannot find development files for any supported version of libnl.  Stop.


This suggests you need to install the "libnl-dev" package (available in Software Center or "sudo apt-get install libnl-dev").

But let's back up a moment. What are you trying to install, where did you get it, does it come with any installation instructions?

---

### Post by Alphamonkey on 2011-11-21
> **snowpine said:**
> This suggests you need to install the "libnl-dev" package (available in Software Center or "sudo apt-get install libnl-dev").

But let's back up a moment. What are you trying to install, where did you get it, does it come with any installation instructions?

Well I recently switched from fedora 15 to ubuntu 11.10. While in fedora I was playing around with aircrack-ng (before you ask only on a network I was authorized to access). I tried using airmon-ng in ubuntu and it gave me the message that said I needed the IW file. In order to download it I just typed wget and the link that it directed me to. After extracting it I tried to "make" it as directed in the readme:

This is 'iw', a tool to use nl80211.


To build iw, just enter 'make'. If that fails, set the
PKG_CONFIG_PATH environment variable to allow the Makefile
to find libnl.


'iw' is currently maintained at [http://git.sipsolutions.net/iw.git/](http://git.sipsolutions.net/iw.git/),
some more documentation is available at
[http://wireless.kernel.org/en/users/Documentation/iw](http://wireless.kernel.org/en/users/Documentation/iw).

Please send all patches to Johannes Berg <johannes@sipsolutions.net>
and CC [email]linux-wireless@vger.kernel.org[/email] for community review.

and thats where I encountered the other error.

About to install the other dev package to see if it works.

thanks for the reply.

---

### Post by snowpine on 2011-11-21
'iw' is in the Ubuntu 11.10 repositories and can be installed through the Software Center or 'sudo apt-get install iw'.

---

### Post by Alphamonkey on 2011-11-21
Well now I feel kind of dumb for going about it the hard way. I am still somewhat new to linux beyond the GUI. I have been trying to learn though. Anyways airmon-ng works now I can start the interface and I am also able to make files, so thank you very much for your help.

---

### Post by snowpine on 2011-11-21
You're welcome and good luck! :)

---

