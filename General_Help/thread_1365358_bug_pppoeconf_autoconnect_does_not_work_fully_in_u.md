---
title: "bug: pppoeconf autoconnect does not work fully in ubuntu 9.10"
date: 2009-12-27
forum: General Help
---

### Post by q.dinar on 2009-12-27
hello.
when i have installed ubuntu 9.10 now internet connected with pppoeconf with option to automatically connect on OS start does not work properly: it connects on start but when when i open site in firefox it cannot find server, if i start empathy it cannot connect, but "host example.com" works and says some ip addresses, if try ping that ip adress it works but if try ping example.com it also cannot find it. all these start to work after "sudo poff dsl-provider" and then "sudo pon dsl-provider".

---

### Post by q.dinar on 2009-12-27
"Report a bug " button in
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
has sent me to
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
from that i have opened
[https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)
from there i have opened
[https://launchpad.net/ubuntu/+search](https://launchpad.net/ubuntu/+search)
there i have searched /etc/network/ and /etc/network/intefaces
and it has found no package about that.
so i do not know right package to send report with "ubuntu-bug <package name>" and cannot simply write about this in the bug tracker, may be bug is in pppd process? hm that package searcher site cannot find also /usr/sbin/pppd so i should search right package with other tool , i am going to try with google and synaptic ... ok i have found "ifupdown" with synaptic.... ok i have successfully runned "ubuntu-bug ifupdown" and now report form has been(?) opened in browser.

13:50 utc+3 : there is bug report: [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/500735](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/500735) .

---

