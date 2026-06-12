---
title: "&quot; mptscsih: ioc0: attempting task abort! &quot;"
date: 2009-12-15
forum: General Help
---

### Post by jumpjumpholydiver on 2009-12-15
Hi,
I'm running Ubuntu 8.04 on a VmWare ESX 3.5. ESX is runnning on a Dell Power Edge 2950 and the VM for this server is on a NetApp LUN. 
This server runs Apache and Jasper reporting tools.
Last night at about midnight it become unresposive....the server was up and I was able to ping it, but Apache and Jasper were not working. 
Anyhow, this is what I found in the syslog from the time teh crash occurred:

[COLOR=Red]

Dec 15 00:02:11 intranet kernel: [9124102.865551] mptscsih: ioc0: attempting task abort! (sc=f54e1500)
Dec 15 00:02:11 intranet kernel: [9124102.865564] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 00 00 5b 8f 00 00 18 00
Dec 15 00:02:12 intranet kernel: [9124103.145568] mptscsih: ioc0: task abort: SUCCESS (sc=f54e1500)
Dec 15 00:02:41 intranet dovecot: pop3-login: Aborted login (0 authentication attempts): rip=10.3.0.18, lip=10.5.0.27
Dec 15 00:02:43 intranet dovecot: imap-login: Aborted login (0 authentication attempts): rip=10.3.0.18, lip=10.5.0.27
Dec 15 07:45:32 intranet syslogd 1.5.0#1ubuntu1: restart.[/COLOR]


This 7:45 restart was done by me. Does anyone have any idea what the "[COLOR=Red]mptscsih: ioc0: task abort: [/COLOR]" stuff is all about?  Everything I'm seeing online points to this being an issue with an LSI Logic SAS card, but this is a VM, so I'm not sure how that would apply.

Any insight into this would be greatly appreciated.
Thanks!

Aaron

---

### Post by feutete on 2009-12-15
I saw these same sorts of errors this morning on a VM running 8.04.2 on ESX4.0. The cause was a loss of network connectivity to our NetApp for about 5 seconds. Do you have any evidence that there may have been a network problem at the time this occurred?

---

