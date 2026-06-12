---
title: "Restricting admin access to mounted USB drive."
date: 2010-06-11
forum: General Help
---

### Post by lakshyaman on 2010-06-11
I have a 1TB USB2.0 external Hard Drive which I want to use for both secure personal file storage and for multi-user backups. The HD has two partitions - one of which is encrypted. 

The drive is to be permanently connected to an always-on computer and the unencrypted partition will shared on the local network for all local users to use for storage/backups as they please. I want to be able to access the encrypted partition over the Internet using SSH.

My problem is how to fix it so that I can SSH into the host computer & mount the encrypted drive whilst ensuring that no one else using the host computer can also see the encrypted files - including the root account. Basically I'm looking for the host computer just to act as an access conduit to the encrypted partition.

Is this possible? Or perhaps is there a better way of sharing part of the HD locally while I can have secure remote (over Internet) access to another part?

Many thanks for reading, I look forward to your suggestions :-)

---

### Post by bodhi.zazen on 2010-06-11
Restricting the root account is the hard part. You would need to use Apparmor to restrict root.

When you ssh in, issue the w command to see who is logged in.

```
w
```

Do not configure the ecnrypted partition as part of the network share (are you using samba ? NFS ? FTP ? what to share the drive ? )

---

