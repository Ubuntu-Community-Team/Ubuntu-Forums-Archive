---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-04-15
forum: General Help
---

### Post by korovacow on 2012-04-15
Hi! I've spent a bit of this weekend setting up Ubuntu server (initially to serve as a NAS, hopefully will replace my router once I pick up some shiny new ethernet cards). During this process I've encountered this "*dpkg returned an error code (1)*" error multiple times (every time I've installed or upgraded anything, I think), and while it doesn't seem to be preventing things from working I am a bit concerned by it.

Searches for a solution suggest that the cause differs from case to case, and as such I humbly request some advice. Here's the most recent occurrence, occurring when I attempted upgrading via apt-get:

```
alex@korova-milkbar:~$ sudo rm -f /etc/samba/smb.conf
alex@korova-milkbar:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ...
Administrator password will be set randomly!
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)


```I've tried removing smb.conf as suggested, to no avail.

I'm on Server 11.10. Let me know if more info is required.

---

### Post by korovacow on 2012-04-20
I'm not sure what is acceptable here in terms of bumping threads, but it's been a week, so... :)

I'm having a lot of trouble getting Samba configured and I'm becoming increasingly convinced that this has something to do with it, but removing/purging and installing again doesn't seem to help.

---

### Post by korovacow on 2012-04-22
Still no progress. Can anyone help with this please?

---

### Post by Headfirst on 2012-04-25
Aww I was hoping someone would've replied to this. I'm having the exact same issue using Ubuntu Desktop not the Server but still v11.10.

---

### Post by korovacow on 2012-04-26
I got all excited about having a reply there. :D

Anyone?

---

