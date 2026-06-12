---
title: "Hostname recognition by a Windows network? Help!"
date: 2006-04-06
forum: General Help
---

### Post by bencrouse on 2006-04-06
Hello,

I'm trying to get my Ubuntu machine to be recognized by hostname across our colleges network.  I've set the hostname everywhere I can find (config files, GUI configurations), and followed the guide for netBIOS names (I included WINS in nsswitch.conf, installed winbind), and still no luck.
It seems to me that the DNS servers here aren't ever seeing my hostname.  I'm not sure why though, which is where I'd like some help.)
I can ping my IP address fine, but all it ever says is cannot find hostname or something to that effect.

Any ideas?

Thanks,
Ben

---

### Post by Pred on 2006-04-24
I've had this same problem at work with a few Ubuntu machines I just built. I ended up finding the solution on here after about 2 weeks of trying to fix it. I fixed mine by changing a line in the dhclient.conf file in /etc/dhcp3 directory. The line is:

#send host-name "andare.fugue.com";

I changed it to:

send host-name "adsales1.hg.internal";

so when you ping a computer on your network, just enter it inplace of hg.internal, know what I mean?

---

