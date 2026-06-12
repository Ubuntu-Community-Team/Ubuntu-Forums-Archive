---
title: "Mounting a NFS share on boot takes aaaaaages"
date: 2006-05-12
forum: General Help
---

### Post by speedsix on 2006-05-12
Added an entry to my fstab to mount an NFS share which works fine but it now takes ages at the 'mounting remote filesystems' step during boot. Atleast a minute.


Thanks

Dom

---

### Post by AndyCooll on 2006-05-12
Please post your /etc/fstab so we can check the settings and such

:cool:

---

### Post by pillypoon on 2006-05-12
[QUOTE=speedsix]Added an entry to my fstab to mount an NFS share which works fine but it now takes ages at the 'mounting remote filesystems' step during boot. Atleast a minute.


Thanks

Dom[/QUOTE]


Install "portmap" and it should be almost instant.

Pilly

---

### Post by ZylGadis on 2006-05-12
Or even better, use sshfs instead of nfs :)

---

### Post by pillypoon on 2006-05-12
[QUOTE=ZylGadis]Or even better, use sshfs instead of nfs :)[/QUOTE]

Just curious if I used sshfs would I still be able to mount my shared drive and stream music/videos to other comps?  Or is it meant just for file transfer?

---

### Post by ZylGadis on 2006-05-12
ssh can be used for file transfers by means of sftp. sshfs , which is a fuse extension to ssh, can be used for actually mounting partitions and accessing them as if they were local - much like nfs. There is a howto on the forums, search for "howto sshfs". There are some drawbacks - mainly stemming from the fact that df does not get the free space of the sshfs partition. For example, if you try copying something in nautilus, it will say "no free space on target" or something like that, so you'd have to cp it in a terminal. That is a very small glitch, though, compared to the absolute easiness to install and maintain sshfs, knowing it is completely secure unlike nfs, and not dealing with matching userids or installing nis or whatever else you need to do with nfs :) 
I can say my home network productivity has doubled since I discovered sshfs.

---

### Post by pillypoon on 2006-05-12
[QUOTE=ZylGadis]ssh can be used for file transfers by means of sftp. sshfs , which is a fuse extension to ssh, can be used for actually mounting partitions and accessing them as if they were local - much like nfs. There is a howto on the forums, search for "howto sshfs". There are some drawbacks - mainly stemming from the fact that df does not get the free space of the sshfs partition. For example, if you try copying something in nautilus, it will say "no free space on target" or something like that, so you'd have to cp it in a terminal. That is a very small glitch, though, compared to the absolute easiness to install and maintain sshfs, knowing it is completely secure unlike nfs, and not dealing with matching userids or installing nis or whatever else you need to do with nfs :) 
I can say my home network productivity has doubled since I discovered sshfs.[/QUOTE]

Ill give it a shot this weekend.. 

What makes NFS so insecure?

---

