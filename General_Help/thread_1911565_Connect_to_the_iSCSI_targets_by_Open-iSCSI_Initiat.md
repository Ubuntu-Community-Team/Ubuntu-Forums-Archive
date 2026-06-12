---
title: "Connect to the iSCSI targets by Open-iSCSI Initiator on Ubuntu Linux"
date: 2012-01-19
forum: General Help
---

### Post by Nikolai D. on 2012-01-19
Hi all,

Just was following this guide
[http://www.qnap.com/pro_application.asp?ap_id=135](http://www.qnap.com/pro_application.asp?ap_id=135)
to connect my FOG server to the QNAP iscsi.

And it says:
** You can delete the node(s) you don’t want to connect to when the service is on with the following command:

# iscsiadm -m node --op delete --targetname THE_TARGET_IQN


My question is: This is not going to delete the LUN itself right? Just to be sure. Its going to just remove unneeded nodes from the list right? So that it doesnt go connecting to nodes i dont need?

Thanks in advance,
Yours,
Nikolai

---

### Post by Nikolai D. on 2012-01-19
Ok, ive deleted the nodes i dont want to connect to.

But then it says to restart the iscsi, and it says:

# /etc/init.d/open-iscsi restart
You should be able to see the login message as below: Login session [iface: default, target: iqn.2004-04.com:NAS:iSCSI.ForUbuntu.B9281B, portal: 10.8.12.31,3260] [ OK ]
Check the device status with dmesg.

But i dot see this message. I see just this:

root@V-FOGUNTU:~# /etc/init.d/open-iscsci restart
 * Disconnection iSCSI targets                      [OK]
 * Stopping iSCSI initiator service                 [OK]
 * Starting iSCSI initiator service iscsid          [OK]
 * Setting up iSCSI targets                         [OK]


So what now?

---

### Post by Nikolai D. on 2012-01-19
ok this command:
iscsiadm -m node -l

from here 
[http://groups.google.com/group/open-iscsi/browse_thread/thread/80e3eee8cdf561a](http://groups.google.com/group/open-iscsi/browse_thread/thread/80e3eee8cdf561a)

made the nodes logged in :)

lets see what do we do next.

---

### Post by Nikolai D. on 2012-01-19
ok, solved it, with the help from here:
[http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target)

---

