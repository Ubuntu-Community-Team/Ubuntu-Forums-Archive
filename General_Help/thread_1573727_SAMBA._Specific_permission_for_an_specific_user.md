---
title: "SAMBA. Specific permission for an specific user"
date: 2010-09-13
forum: General Help
---

### Post by ^_Pepe_^ on 2010-09-13
Hi all.

This is my situation and what I want to do (and I don't know how to)

I have a beatiful 6-computer LAN (ethernet and Wifi based) with an Ubuntu server, some Windows (HTPC and Gamer) and Ubuntut boxes (laptops).

Al information is in serveral disks in server /media/MYINFORMATION (let's say), and this is shared with SAMBA (for windows, and sometimes for Linux) and NFS (for fstab linux mounts, since samba fstab-mounts with Wifi have an unresolved bug to shutdown). I have no special permissions inside my network, I mean there're no passwords for samba shares.

I want to create a new user (myfriends, let's say) and a new share filesystem, /media/MYINFORMATION/guestshared, to be shared through sftp for this new user (desktop user), and let this user to reach only this filesystem, but not the rest of information.

Can I get this configuration easily or should I password-protect all the rest of information? (A mess to me...)

Thanks in advance,

Best regards,
^_Pepe_^

---

