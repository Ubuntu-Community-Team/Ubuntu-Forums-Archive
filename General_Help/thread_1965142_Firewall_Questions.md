---
title: "Firewall Questions"
date: 2012-04-25
forum: General Help
---

### Post by vanquishedangel on 2012-04-25
Ok I know that firestarter is considered dead and most people say to use gufw but here are my questions

1. Firestarter is way more configurable than gufw (i mean by clicking buttons) so really isn't it better that way?

2. With either of these programs is the firewall running with the settings you put in when the gui is closed (are the rules still applying)?

3. Way back (i mean way back) I used safety.net for windows xp and it was the best windows firewall ever, is there a user interface in ubuntu that is similar to that one, or zonealarm? ( i mean for iptables)

---

### Post by mangmista on 2012-04-25
do you really need firewall?

---

### Post by vanquishedangel on 2012-04-25
> **mangmista said:**
> do you really need firewall?

in short...yes, iptables acts/is a firewall and I just would like to configure it :) and so all ubuntu has it.

---

### Post by Lars Noodén on 2012-04-25
[fwbuilder](http://www.fwbuilder.org/) is another option, besides GUFW.  Or you could just work directly with IPTables, either via a shell script or via [iptables-save](http://manpages.ubuntu.com/manpages/oneiric/en/man8/iptables-save.8.html) + [iptables-restore](http://manpages.ubuntu.com/manpages/oneiric/en/man8/iptables-restore.8.html).

---

### Post by houseworkshy on 2012-04-25
One doesn't have to worry about either if one simply uses ufw, it's actually very clear.  "man ufw" in the terminal for details.

---

