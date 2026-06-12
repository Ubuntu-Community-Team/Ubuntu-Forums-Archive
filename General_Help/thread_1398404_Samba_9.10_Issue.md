---
title: "Samba 9.10 Issue"
date: 2010-02-04
forum: General Help
---

### Post by Paulie-9 on 2010-02-04
All - 

I had a box running 9.04 that I upgraded to 9.10 and I cannot print or browse to shared drives from my iMac.  I have several other Macs and PCs that work fine.  This was the first that I setup to print on 9.04.  I have attempted everything that I can find including installing in CUPS, using the ip address, etc.    I can browse to workgroup and I see the computer but when I try to use either USERID guest or userid/passwd - I get no response.  

I looked in the /var/log/samba for this computer and here is what I am getting for an attempt:


[2010/02/04 12:09:08,  1] ../librpc/ndr/ndr.c:374(ndr_pull_error)
  ndr_pull_error(11): ndr_pull_advance by 469762046 failed
[2010/02/04 12:09:08,  1] ../librpc/ndr/ndr.c:374(ndr_pull_error)
  ndr_pull_error(11): Pull bytes 2
[2010/02/04 12:09:08,  0] rpc_server/srv_pipe.c:2332(api_rpcTNP)
  api_rpcTNP: \srvsvc: SRVSVC_NETSHAREENUMALL failed.

I have beat my head in on this and I am at a point that I am confused.  Can someone help?

---

### Post by jken146 on 2010-02-05
Have you read [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) ?

---

