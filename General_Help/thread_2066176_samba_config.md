---
title: "samba config"
date: 2012-10-03
forum: General Help
---

### Post by mattmann on 2012-10-03
Hi, I've been running Ubuntu12 for about 48hrs and love it! However I am having difficulty getting windows shares to mount automatically. I have to say that the samba docs are overwhelming when what I want to do is soooo simple. I can use the 'Connect to server...' in the file manager without probs, but can't seem to convert this into sambaspeak.

Here are my 'Connect to server...' settings used in file manager

Server:       MR-PRESIDENT
Type:           Windows share
Share:          FileXchange
Foder:          /

Domain name:     MYDOMAIN.COM
Username:             me
Password:              mypassword

I just can't seem to get this right in smb.conf. I've tried the Samba Config Too; as well but it just tells me there is no such directory.
Windows server running Server2008 which is the one and only domain controller.

Your help would be greatly appreciated.

---

### Post by bab1 on 2012-10-03
> **mattmann said:**
> Hi, I've been running Ubuntu12 for about 48hrs and love it! However I am having difficulty getting windows shares to mount automatically. I have to say that the samba docs are overwhelming when what I want to do is soooo simple....

What is it that you're trying to do?  How many hosts are in this network.  What is the OS of the client machine (i.e. Windows 7 or XP).  Could it be that you are trying to mount the share to the server from the very same server?

In other words -- more info please regarding you situation.

---

