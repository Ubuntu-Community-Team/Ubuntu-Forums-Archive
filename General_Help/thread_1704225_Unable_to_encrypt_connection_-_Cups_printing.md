---
title: "Unable to encrypt connection - Cups printing"
date: 2011-03-10
forum: General Help
---

### Post by unix_boy on 2011-03-10
I am seeing the following errors in my cups server error.log when I try to print from an SAP client. From the SAP server, I am able to print to the same printserver/printer by using lp -d, however, when printing from SAP I get this error. SAP does sound to be the suspect, by why would cups try to encrypt?...and from the cups side, what does encrypt_client: A record packet with illegal version was received. usually mean?

E [09/Mar/2011:16:08:34 -0400] encrypt_client: Unable to encrypt connection from 172.16.90.50!
E [09/Mar/2011:16:08:34 -0400] encrypt_client: A record packet with illegal version was received.

The only changes to default cups.conf on server:

Listen <ip>:631

The only changes made to default cups.conf on client:
BrowsePoll 172.16.90.14

---

### Post by unix_boy on 2011-03-10
... very similar to this one:

[http://ubuntuforums.org/archive/index.php/t-530018.html](http://ubuntuforums.org/archive/index.php/t-530018.html)

---

### Post by beatskobe on 2011-03-10
i hope it come on

---

