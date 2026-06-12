---
title: "postfix for local network"
date: 2012-01-06
forum: General Help
---

### Post by Drenriza on 2012-01-06
Hey guys.

I have installed Ubuntu server 11.10, with postfix. What i would like to, is create a postfix server which can send (NOT RECEIVE) e-mails to users on a local network. But i have never setup a mail server before. So can someone point me in the direction of a guide that can allow me to do this?

Or can you explain what i need to do to accomplish this :p?

Thanks on advance.
Kind regards.

---

### Post by lechien73 on 2012-01-06
Is your postfix server relaying to the Internet, or is this for a small internal mail system?

There's a guide to setting up postfix on Ubuntu here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by Drenriza on 2012-01-06
> **lechien73 said:**
> Is your postfix server relaying to the Internet, or is this for a small internal mail system?

There's a guide to setting up postfix on Ubuntu here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Not sure what relaying to the internet means, in terms of mail servers. The physical server itself got a WAN connection. But the postfix server is only to work on the local network. And should not send or receive anything to / from the public network (WAN) and only send and not receive on the local network.

Also from what i know. The postfix docent need authentication setup. Since it is not to receive e-mails at all.

---

### Post by dcstar on 2012-01-07
> **Drenriza said:**
> Not sure what relaying to the internet means, in terms of mail servers. The physical server itself got a WAN connection. But the postfix server is only to work on the local network. And should not send or receive anything to / from the public network (WAN) and only send and not receive on the local network.

Also from what i know. The postfix docent need authentication setup. Since it is not to receive e-mails at all.

```
sudo dpkg-reconfigure postfix
```

Assuming you only want it to send mail generated on the server it is on set the only IP address to accept messages to the localhost - 127.0.0.1

---

