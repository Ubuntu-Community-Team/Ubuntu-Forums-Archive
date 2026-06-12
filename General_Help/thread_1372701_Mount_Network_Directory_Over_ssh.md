---
title: "Mount Network Directory Over ssh ??"
date: 2010-01-04
forum: General Help
---

### Post by WorldTripping on 2010-01-04
Hi,

I'm wondering if there is a solution to this ?

I have a Sheevaplug attached to my router and a 1.5 TB external HDD.

I can ssh into the HDD over my LAN (ssh user@LAN:IP:ADDRESS).

I can mount a directory from the HDD to a laptop over the LAN (fstab rules).

I can ssh into the HDD remotely (ssh user@ROUTER:IP:ADDRESS

However I cannot mount any directories from the HDD (!?)

What am I missing ?

My fstab entry goes like this:
ROUTER:IP:ADDRESS:/media/STORY /home/simon/STORY nfs rw 0 0

And I get this error:
'mount.nfs: mount system call failed'

On the server my /etc/exports looks like this:
'/media/STORY *(rw,no_root_squash,async)'

Anyone any ideas on how I can mount a directory from a server behind a router remotely (ie outside the LAN) ?

Cheers in advance.

WorldTripping

---

### Post by jkounis on 2010-01-04
> **WorldTripping said:**
> 
Anyone any ideas on how I can mount a directory from a server behind a router remotely (ie outside the LAN) ?


It's not entirely clear what your configuration is, but it appears that you're trying to get an nfs mount to traverse a router (possibly with NAT?). My guess is you need to make sure that port 2049 for nfs is forwarded to the correct server (the NFS server). You may also need to forward port 111 for RPC. I'm not sure if this is necessary for NFS.

But be very careful. Port 111 is a common port for attacks. If an attacker discovers this open port, you may be vulnerable if your security isn't up to snuff.

---

### Post by bodhi.zazen on 2010-01-04
If you can ssh in , use sshfs:

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by WorldTripping on 2010-01-04
> **jkounis said:**
> It's not entirely clear what your configuration is, but it appears that you're trying to get an nfs mount to traverse a router (possibly with NAT?). My guess is you need to make sure that port 2049 for nfs is forwarded to the correct server (the NFS server). You may also need to forward port 111 for RPC. I'm not sure if this is necessary for NFS.

But be very careful. Port 111 is a common port for attacks. If an attacker discovers this open port, you may be vulnerable if your security isn't up to snuff.

Still giving me a 'mount.nfs: mount system call failed' error when mounting.

Cheers though, and I'll look into security, Ta.

Worldtripping.

---

### Post by WorldTripping on 2010-01-04
> **bodhi.zazen said:**
> If you can ssh in , use sshfs:

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

Ah, OK, I'll have a read now.

Thanks,

WorldTripping

---

### Post by WorldTripping on 2010-01-04
> **bodhi.zazen said:**
> If you can ssh in , use sshfs:

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

That worked perfectly.

Thanks, that has just ended a day long quest for me.

Ta.

WorldTripping.

---

### Post by bodhi.zazen on 2010-01-05
> **WorldTripping said:**
> That worked perfectly.

Thanks, that has just ended a day long quest for me.

Ta.

WorldTripping.

Glad you got it sorted.

Over a LAN you can use NFS or Samba.

Over the Internet use sshfs, sftp, or scp (all variants of ssh). From windows you can use Putty / Winscp (although if you use openssh keys you will need to import them to putty / winscp).

---

