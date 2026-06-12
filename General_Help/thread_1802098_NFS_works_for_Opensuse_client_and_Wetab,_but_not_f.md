---
title: "NFS works for Opensuse client and Wetab, but not for Kubuntu and Xubuntu"
date: 2011-07-11
forum: General Help
---

### Post by twyufe on 2011-07-11
I've updated my Asus-router RT-16n with the latest OLEG-firmware of 3th of July. Connected to this router are 2 USB-harddisks and one of them is shared through NFS.

Now I am having trouble to get the NFS-server on my RT-16n to work for all clients. The following command works from Opensuse and my Wetab: sudo mount -t nfs -o vers=3,tcp,lock,intr,hard,rw,nolock 192.168.123.1:/mnt/nfs-data/ /Asus
In syslog.log: mountd[365]: authenticated mount request from 192.168.123.103:909 for /mnt/nfs-data (/mnt/nfs-data)

However from Kubuntu 11.04 and Xubuntu 11.04 I get on the client side: mount.nfs: access denied by server while mounting 192.168.123.1:/mnt/nfs-data/
In syslog.log:mountd[365]: refused mount request from EEElaptop for /mnt/nfs-data (/): no export entry

My only exports-line is: /mnt/nfs-data 192.168.123.*(rw,async,insecure)

Why the ubuntu-variants won't connect, is beyond me. :confused:
Anyone an idea?

---

### Post by smurphy_it on 2011-07-11
Ubuntu derivatives on same vlan ?  what does "sudo showmount -e 192.168.123.1" display on those boxes ?

---

### Post by twyufe on 2011-07-15
"sudo showmount -e 192.168.123.1" replies with: /mnt/nfs-data 192.168.123.*

Is correct.

---

### Post by Zill on 2011-07-15
> **twyufe said:**
> ...My only exports-line is: /mnt/nfs-data 192.168.123.*(rw,async,insecure)
You could try changing the exports line to
```
/mnt/nfs-data 192.168.123.0/24(rw,async,insecure)
```
which should cover the range 192.168.123.0 to 192.168.123.255

Of course, after making changes to /etc/exports in a terminal you must type
```
sudo exportfs -a
```

---

### Post by twyufe on 2011-07-18
Thanks for the advice, but that didn't work as well. However I found it. The error has to do with the Asus RT-16N router (which is a server as well) not being able to resolve the IP address of both PC's. For both PC's were I had created fixed IP addresses for their MAC-addresses in the Asus router, with an earlier firmware version. 

After updating the firmware of the router this caused the problem, although it gave both PC's the right IP address. Removing both fixed IP addresses made it working again. It is more or less a bug in the OLEG-firmware of the RT-16N (and other WL500-routers with the same kind of firmware).

Glad I found it  :P

---

### Post by twyufe on 2011-07-19
And in the end it wasn't the Asus router after all, as one PC continued to have a problem. It needed to have these options to run:

mount -t nfs -o vers=3,tcp,nolock,intr,hard,rw,noauto 192.168.123.1:/mnt/nfs-data/ /Asus

:confused::confused:

---

### Post by Zill on 2011-07-19
twyufe:  I am pleased you have got it working and thanks for posting the outcome.

Please use the "Thread Tools" menu at the top of this page to mark the thread as solved to help other users searching with similar problems.

---

