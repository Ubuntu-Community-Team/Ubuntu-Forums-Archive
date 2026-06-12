---
title: "Unable to install anything"
date: 2010-01-17
forum: General Help
---

### Post by Ganesho on 2010-01-17
Any time i try to install anything from terminal or synaptic i get this error message saying:

/usr/bin/dpkg: 1: Syntax error: ")" unexpected
E: Sub-process /usr/bin/dpkg returned an error code (2)

or if i try to upgrade:

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
26 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
/usr/bin/dpkg: 1: Syntax error: ")" unexpected
E: Sub-process /usr/bin/dpkg returned an error code (2)


If i try to open the software-center the cursor changes but it does not open. This all started when it upgraded to Karmic Koala. There might be two seperate issues but i cannot install or uninstall at all. Thanks for your help.

---

### Post by Easy Limits on 2010-01-17
Did you try sudo apt-get update first before sudo apt-get upgrade?

---

### Post by Ganesho on 2010-01-17
Thanks for your reply, yes i did an update first but i believe it all originated with an update with the update manager and that is a while back. I cannot install anything right now. The software center does not open or seems to crash on opening. I am also not able to install anything with the synaptic package manager. I get the same error as above.

/usr/bin/dpkg: 1: Syntax error: ")" unexpected
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

