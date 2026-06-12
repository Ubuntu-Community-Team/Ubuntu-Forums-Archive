---
title: "LTSP with Ubuntu 10.04 - Simple solution to make it work !"
date: 2011-01-27
forum: General Help
---

### Post by adallaire on 2011-01-27
Hi everyone,

I've been trying to install an LTSP server on 10.04 and just didn't find why it doesn't work out-of-the-box like it's supposed to...  I just kept having errors like these ones :

"PXE-E51 : No DHCP or proxyDHCP offers were received." when a thin client boots.  So I manually started the DHCP server using "sudo /etc/init.d/dhcp3-server start".  Ok.

Then...

When booting a thin client again, I had an "Error : failed to connect to NBD server."  So I searched forums for hours to find an answer...  but didn't found one.

Then I noticed that a lot of people seemed to have it work easily with Karmic 9.10 but when installing/upgrading to 10.04, they got stuck with many issues.

I reinstalled 10.04 a couple of times to finally have myself scanning used ports on the server...  and realize that the famous port 2000 used by the NBD server was already used (and pre-configured by the Ubuntu installer) by "cisco-sccp" service, which seems to manage VoIP or something like that.  So I opened the /etc/services file and scanned for that 2000 port and yes, it was associated to cisco-sccp so I simply changed it to 2001.  I then restarted the server and voilà !, dhcp3-server started automatically so does the NBD server !   Then I tried my thin clients and everything just worked fine.

How come the "LTSP server install" of the alternate CD does not take this into account and automatically assign cisco-sccp to another port than 2000 ?  And was the cisco-sccp service existing in 9.10 anyway ?  I scanned the ports on my laptop which is using Karmic and didn't find it.  Would that be why it seems to work out-of-the-box on Karmic ?

Anyways, everything works fine now and I just wanted to share my solution (pretty simple) with everyone.

Hope this helps !   :P

Cheers,

---

