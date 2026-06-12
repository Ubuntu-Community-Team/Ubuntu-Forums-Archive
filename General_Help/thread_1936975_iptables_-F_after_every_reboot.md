---
title: "iptables -F after every reboot"
date: 2012-03-07
forum: General Help
---

### Post by Kissell on 2012-03-07
I messed up and did something I shouldn't have with iptables.  

Now everytime I reboot, I can't web browse until I do "iptables -F"

I don't care about any of the rules in iptables.  Is there a way I can get this change to become permanent?

---

### Post by raja.genupula on 2012-03-07
may be this
[http://parkyjimbo.blogspot.in/2010/06/iptables-lost-after-reboot-of-head-node.html](http://parkyjimbo.blogspot.in/2010/06/iptables-lost-after-reboot-of-head-node.html)

---

### Post by kevdog on 2012-03-07
There's a few ways you can accomplish this depending on how you set up your iptables.  I usually load all my iptables from a script file, so I just put the script file within /etc/rc.local so it's run as root.  The post that references another method likely works just as well.  The reason I do it the way I do it, is that I often have to modify the script -- I screw up something, or want to make something more/less restrictive.  If I just edit the file and save the changes, I'm guaranteed the changes are there on next boot without the extra step of having to remember to export the currently loaded iptable ruleset.

---

### Post by Kissell on 2012-03-07
Thanks guys.  

I saved my good rules at "iptables-save > /etc/iptables.rules" as that blog post suggested...  that should do it I think...  if it reads that file on startup.  Can't reboot right now though...  internet too important.

---

### Post by raja.genupula on 2012-03-07
Give a try my friend , IF that one fixed your issue then you will be fine . ok do restart at your free times and report us back if you got any .

---

### Post by Kissell on 2012-03-12
That link was just describing how to save the iptables rules to a file, the system doesn't look in that location for the rules at boot time.  

I just ended up adding "iptables -F" to /etc/rc.local

---

