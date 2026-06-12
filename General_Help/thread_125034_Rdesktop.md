---
title: "Rdesktop"
date: 2006-02-02
forum: General Help
---

### Post by chadwick359 on 2006-02-02
I would like to be able to use rdesktop to remote into the (Windows) machines in my office so i can be lazy and do work from my comfy chair, but I have a bit of a problem. I don't know where to point rdesktop. All of the machines are on a internal network, and I don't know how to point rdesktop at that network, then the machine. Could somebody tell me how to look up the correct domain to give to rdesktop?

---

### Post by darth_vector on 2006-02-02
you wont be able to unless you are the admin of the office network or have their blessing.

the gateway at the office network will have to have a redirect set up on the firewall or  to accept remote desktop connections. in the second case you would initiate a second remote desktop connection from the gatway to your office pc.

---

### Post by chadwick359 on 2006-02-02
Fortunatley for me, the machines accept remote desktop connections, and I am on the It team, so I do have admin access.

---

### Post by darth_vector on 2006-02-02
then you will have to arrange for a redirect to be set up for you or you will have to remote desktop to an intermediary gateway server and then remote desktop from that to your office machine.

---

### Post by chadwick359 on 2006-02-02
Okay, I figured as much. Thanks a lot.

---

