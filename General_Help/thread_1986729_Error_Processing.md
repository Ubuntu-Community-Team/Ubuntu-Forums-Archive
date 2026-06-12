---
title: "Error Processing"
date: 2012-05-25
forum: General Help
---

### Post by Renjith Jithu on 2012-05-25
Hi

We are under the upgrade of oscar 9 to oscar 12.While executing the step

sudo dpkg -i oscar-mcmaster12.2.5release

we got the error like this

dpkg:error processing oscar-mcmaster (--install) :
subprocess post-installation script returned error exit status 1
Error were encountered while processing:
oscar-mcmaster

   Anybody have any idea about problem please help me.

Renjith

---

### Post by kc1di on 2012-05-25
in your file browser navigate to the following /var/lib/dpkg/info/
and see in the list there if there is a script with the name of your program. if there is delete it and try to install again.

---

