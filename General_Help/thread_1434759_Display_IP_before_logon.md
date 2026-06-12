---
title: "Display IP before logon"
date: 2010-03-20
forum: General Help
---

### Post by cbuhler on 2010-03-20
Hello,

I am running Ubuntu 9.10 server and I am trying to get the IP address of the machine to display at boot (before login) but so far no luck. Here is what I have tried:

Created a script called displayip:

#!/bin/sh
ifconfig eth0 | grep "inet addr:" | awk -F'inet addr:' '{print $2}'

which is located in the /etc/init.d directory.

changed the permissions to make it executable:

chmod +x displayip

then ran update-rc.d displayip defaults which ran successfully.

Upon boot it doesn't show up with anything. If someone could point me in the right direction that would be great.

---

### Post by gmargo on 2010-03-20
The directory /etc/network/if-up.d/ holds scripts that get run when a network interface comes up.  Details in the **interfaces(5)** man page.

---

