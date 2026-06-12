---
title: "Sharing internet connection: unclear tutorial"
date: 2009-10-12
forum: General Help
---

### Post by t0p on 2009-10-12
I want to follow t[his tutorial]("https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing") from the Ubuntu Community Documentation so I can share my netbook's wireless connection with my desktop computer.

Unfortunately, the tutorial is unclear about which commands I should run on which computer.  For example:


[LIST]
[*]On which computer do I install dhcpd ("wireless" or "wired")?
[*]On which do I edit dhcpd.conf?
[*]On which do I edit /etc/default/dhcp?
[*]On which do I edit /etc/network/interface?
[*]On which do I add the iptables rule?
[/LIST]
This may all seem self-evident to the author of the tutorial and to many of you.  But I'm a newbie to the mysteries of Linux networking, and it is *not* obvious to me.

If someone could clarify these points for me, I'd be very grateful.  And it might be an idea if someone in the know could edit the tutorial too, lest any other networking n00bs suffer from this confusion.

Cheers!

---

### Post by dcstar on 2009-10-13
> **t0p said:**
> I want to follow t[his tutorial]("https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing") from the Ubuntu Community Documentation so I can share my netbook's wireless connection with my desktop computer.

Unfortunately, the tutorial is unclear about which commands I should run on which computer.  For example:


[LIST]
[*]On which computer do I install dhcpd ("wireless" or "wired")?
[*]On which do I edit dhcpd.conf?
[*]On which do I edit /etc/default/dhcp?
[*]On which do I edit /etc/network/interface?
[*]On which do I add the iptables rule?
[/LIST]
This may all seem self-evident to the author of the tutorial and to many of you.  But I'm a newbie to the mysteries of Linux networking, and it is *not* obvious to me.

If someone could clarify these points for me, I'd be very grateful.  And it might be an idea if someone in the know could edit the tutorial too, lest any other networking n00bs suffer from this confusion.

Cheers!

**All** configuration is done on the PC that will be sharing the connection.

---

### Post by P4man on 2009-10-13
Let's make sure you are following the correct tutorial first. What exactly are you trying to achieve, share a wireless broadband connection over wifi ? A wifi connection over ethernet?

---

### Post by t0p on 2009-10-13
> **P4man said:**
> Let's make sure you are following the correct tutorial first. What exactly are you trying to achieve, share a wireless broadband connection over wifi ? A wifi connection over ethernet?

My netbook has internet connection via wireless.  I want to share that internet connection with my desktop computer via ethernet cable.  Which is the subject of the tutorial.

I know I have got the right tutorial.  I just want someone to clarify the points that I listed in the OP.  But maybe I don't need that now, as dcstar has done that already.

Thanks dcstar!

---

