---
title: "Trouble connecting to QNAP iSCSI target"
date: 2010-11-08
forum: General Help
---

### Post by Thizzle on 2010-11-08
Hi all,

I would like some help connecting to my QNAP iSCSI target from Ubuntu (10.04). I've followed the instructions in the [QNAP manual](http://www.qnap.com/pro_application.asp?ap_id=135), but I something goes wrong when I need to list the nodes.

When I enter ```
# iscsiadm -m discovery -t sendtargets -p 192.168.0.50:3260
```I get the following output:
```
192.168.0.50:3260,1 iqn.2004-04.com.qnap:ts-459:iscsi.lavblue.c47d26
```
Then I enter ```
#iscsiadm -m node
``` and I get the same output as with the previous command:
```
192.168.0.50:3260,1 iqn.2004-04.com.qnap:ts-459:iscsi.lavblue.c47d26
```
According to QNAP's instructions, I should now see a login message, but this is all that appears.

What am I doing wrong? Please help.

---

### Post by Thizzle on 2010-11-12
Okay, I've got it working after following this guide: [http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target)

It's slightly more elaborate and helpful than the instructions posted by QNAP.

---

