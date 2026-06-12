---
title: "Mounting nfs shares"
date: 2012-05-15
forum: General Help
---

### Post by mcollis on 2012-05-15
Hi all,
not sure if this is the correct place for this but here goes.

I've setting up ubuntu to run FreeFileSync between 2 openSUSE servers, unfortunately i'm having a problem with mounting one of the nfs shares.

I have 2 shares being sent:
/data
/etc/samba/admin

For some reason, I can only mount /data using the following command:
mount -t nfs4 -o proto=tcp,port=2049 srv1:/ /srv1/data

and when attempting to mount /etc/samba/admin i get an error stating that the file cannot be found.
I'm thinking that /data is being shared as a root path although i've no idea how to set the names of nfs shares, ie like in window$ you can share c:\windows\temp as \\name\bob
would someone be able to shed a little light on the matter?
before any one says it, unison/rsync are not viable for me.

---

### Post by mcollis on 2012-05-15
Sorry, I should add that it's ubuntu 11.10 and suse 11.3
I've used rsync and unision for some time but found rsync's 1 way feature not what we required and unison has problems since our database became corrupted and its not synced for several weeks now hence a change in direction

---

### Post by roelforg on 2012-05-15
Say the server's ip is 192.168.0.111 and it exports share /shares/myshare
and you want to mount it on ~/share and your user name on the client is mcollis
```

mkdir ~/share
sudo mount -t nfs 192.168.0.111:/shares/myshare /home/mcollis/share

```

---

### Post by mcollis on 2012-05-15
So are you saying it would be best to have 1 folder in the export list and the symlink all my required folders to it?

---

### Post by drdos2006 on 2012-05-15
You can have more than 1 share listed in your /etc/exports configuration file. 
You can also allocate single IPs for reading and writing or reading only, or allocate IP ranges.

For the type of filesystem, I would have thought -t would be ext3 or ext4, not nfs.

regards

---

### Post by SeijiSensei on 2012-05-15
> **mcollis said:**
> I have 2 shares being sent:
/data
/etc/samba/admin

For some reason, I can only mount /data using the following command:
mount -t nfs4 -o proto=tcp,port=2049 srv1:/ /srv1/data

As opposed to what exactly?  The usual approach is to create an entry in /etc/fstab that lists the nfs mount like this:

```
srv1:/  /srv1/data   nfs   defaults,proto=tcp 0 0
```

Now either the share will be mounted automatically when you connect to the network, or you can mount it yourself after connecting the "sudo mount -t nfs -a".

> when attempting to mount /etc/samba/admin i get an error stating that the file cannot be found.

What does the entry in the server's /etc/exports file that lists /etc/samba/admin look like?  Do you have an empty /etc/samba/admin directory on your machine where the share can be mounted?  If not, create it with "sudo mkdir /etc/samba/admin" then try mounting the NFS share again.  The server will need to have that directory exported with the "no_root_squash" option, and you will need to have root permissions to mount it.

---

### Post by mcollis on 2012-05-16
I actually found the cause and all is now sorted.
with NFSv4 shares if you set fsid=0 on any of the exports this becomes the root share and all sub files must be part of this share.
my work around was to set the export dir to /
with the following in my export file:
/ <ip address>(fsid=0,no_root_squash,async,no_all_squash)

As access is bound ONLY to the 1 server behind a secure LAN security is not likely to be compromised and infact any files that we require to sync between the 2 systems can be done so quickly and easily.

Now I can mount the required drives as I require and all is working fine.

If anyone else gets a similar problem the following site helps a lot:
[https://wiki.archlinux.org/index.php/NFSv4](https://wiki.archlinux.org/index.php/NFSv4)

---

