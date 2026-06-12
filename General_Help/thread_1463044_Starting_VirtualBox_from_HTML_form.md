---
title: "Starting VirtualBox from HTML form"
date: 2010-04-26
forum: General Help
---

### Post by sprvn on 2010-04-26
While trying to automate a few things, i have come across this wonderful command that can start a VM from command line as follows "VBoxManage startvm <vmname>"
Now, i ask the user to input the VMname through a HTML form, and run the following perl program (which is the form action). But unfortunately, there seems to be some problem thats not allowing the vm to start when called this way.

#!/usr/bin/perl -w
use CGI qw(:standard);
print "header"
$p=param("vmname");
$c1="VBoxManage startvm $p";
system($c1);

Any solutions or suggestions are welcome, and my apologies if the thread is too long or in inappropriate forum.

---

