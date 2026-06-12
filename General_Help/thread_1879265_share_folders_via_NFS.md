---
title: "share folders via NFS"
date: 2011-11-11
forum: General Help
---

### Post by elmuz on 2011-11-11
Hi there,
we have two Ubuntu computer (11.04) in LAN and we want to share a folder from one machine to be accessible from the other.
The application we use implies the share via NFS and not SAMBA.

After several guides we got only read permissions for the client.

Computers are
131.x.y.98 (server with the folder to be shared)
131.x.y.99 (client which needs to 'rw' on that folder)

...98:/etc/exports with "/var/snd 131.x.y.99 (rw)"

...98:/etc/hosts.allow with "portmap ypserv ypbind : ipserv ipclient"

...98:/etc/hosts.deny empty

I even did a "sudo chmod -R 777 /var/snd"...
The folder seen from the server is belonging to nobody:nogroup...

When I mount from the client that folder I just can navigate the mounted folder but I have read-only permissions..

Any ideas?
Thank you in advance

elmuz

---

### Post by SeijiSensei on 2011-11-11
Are you trying to mount the share on the client as root?  If so, you'll probably need to add "no_root_squash" to the options on the server.  The default is to remap all root mounts to the nobody user.

---

### Post by elmuz on 2011-11-11
I did it via fstab on the client...

131.x.y.98:/var/snd /var/snd nfs,rw,hard,intr 0 0

(the should have same tree "/var/snd" on both machines, sharing same partition)

Anyway I also tried "no_root_squash" and "async" option in /etc/exports with always the same results...

Thank you anyway...

---

### Post by elmuz on 2011-11-11
Oh my God... shame on me!
The mistake was here:
...98:/etc/exports with "/var/snd 131.x.y.99 (rw)"

...I wrote a space between the ip and the privilegies!

SOLVED.

---

### Post by btindie on 2011-11-11
There shouldn't be a space in your /etc/exports file
```
/var/snd 131.x.y.99(rw)
```
then update the export list
```
sudo exportfs -arv
```
You could install autofs which would then allow you to browse the exports.
```
ls /net/hostname
```
You can then just mount /net/hostname/var/snd on /var/snd

---

