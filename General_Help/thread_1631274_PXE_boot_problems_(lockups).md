---
title: "PXE boot problems (lockups?)"
date: 2010-11-26
forum: General Help
---

### Post by rchille on 2010-11-26
Hello all!

I've had a system running well for a while that I wanted to switch to diskless setup. I followed the directions here: [https://help.ubuntu.com/community/DisklessUbuntuHowto]("https://help.ubuntu.com/community/DisklessUbuntuHowto") and finally have most everything working.

Basics of my config:
TFTP/NFS Server at 192.168.1.201
Diskless system at 192.168.1.202
DD-WRT router doing DHCP 192.168.1.1

This config was doing diskless mythbuntu initially and was working. I've just changed the the server to match the directions from above and rebuilt the client. 

What I see when I boot:
DHCP works.
vmlinuz and initrd.img both load.
A bunch of stuff scrolls by that looks like me hardware being detected and loaded.
I get a ```
IP-Config: eth0 complete (from 192.168.1.1)
``` message followed by a lot of status messages about the connection and rootserver. 
I then get:
```
Begin: Running /scripts/nfs-premount ...
Done.
Done.
Begin: Running /scripts/nfs-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
```
This is followed by an error probing SMB2 (which I still have of the disked version of the system)
Then it hangs with re-occurring messages in the form:
```
[  ###.######] INFO: task udevd:### blocked for more than 120 seconds. 
```
Which repeats every 2 mins along with a message on how to disable that message.

I'm stuck in that nothing appears to have been written to any log file that I can find and the messages themselves haven't given me enough of a clue that I can find anything via the forums or Google. 

Switching the boot order to include the Harddrive works.

I've taken a few stabs at fstab thinking that might be the problem (for no other reasons that nfs is the last thing I see talked about and the logs never get updated)

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#UUID=6ce383b0-c657-4254-802b-a608db1e8a55 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=f34cf426-954d-4cf4-a841-55b493c39d4c none            swap    sw              0       0
proc            /proc           proc    defaults        0       0
/dev/nfs       /               nfs    defaults          1       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0

```
(Original lines commended out)


I'm not sure were to even begin, so has anyone seen something similar or have a clue where I can start? 

Thanks!

---

