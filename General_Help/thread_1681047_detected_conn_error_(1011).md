---
title: "detected conn error (1011)"
date: 2011-02-03
forum: General Help
---

### Post by bestorj on 2011-02-03
I am very limited in my use of linux but my company has a ubuntu server running VMware connected to an iscsi san for the datastore. It server appears as if the nic is flapping. Below is the output from tail /var/log/messages. I have tried rebooting the server and reconnecting the iscsi target but I still recive the same issue and it seems to be getting worse.
Any help would be much appreciated.
Thanks
Jason
 
Feb 3 13:45:05 manhattan34 kernel: [ 4054.272767] connection1:0: detected conn error (1011)
Feb 3 13:45:13 manhattan34 kernel: [ 4061.567934] session1: target reset succeeded
Feb 3 13:46:00 manhattan34 kernel: [ 4108.812393] connection1:0: detected conn error (1011)
Feb 3 13:46:04 manhattan34 kernel: [ 4113.117026] connection1:0: detected conn error (1011)
Feb 3 13:46:32 manhattan34 kernel: [ 4140.857905] session1: target reset succeeded
Feb 3 13:48:46 manhattan34 kernel: [ 4275.112008] connection1:0: detected conn error (1011)
Feb 3 13:48:46 manhattan34 kernel: [ 4275.362700] connection1:0: detected conn error (1011)
Feb 3 13:48:50 manhattan34 kernel: [ 4279.154529] session1: target reset succeeded
Feb 3 13:49:50 manhattan34 kernel: [ 4339.330825] connection1:0: detected conn error (1011)
Feb 3 13:50:48 manhattan34 kernel: [ 4396.911289] connection1:0: detected conn error (1011)

---

