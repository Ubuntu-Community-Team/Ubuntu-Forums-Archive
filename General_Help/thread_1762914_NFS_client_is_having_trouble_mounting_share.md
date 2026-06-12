---
title: "NFS client is having trouble mounting share"
date: 2011-05-19
forum: General Help
---

### Post by hoffman462 on 2011-05-19
Hi, I'm far from an NFS expert, or "Linux" Expert, but I've fumbled through it this fa - please and thank you for your help if you can provide it.

I have a couple of NFS clients trying to mount a share on a NFS server.
The server was just upgraded to 11.04 (natty) and one of the clients was also just upgraded to 11.04.

On the client running 11.04 - I'm not able to mount any of the shares that I used to be able to mount.  I can't tell why.  Did NFS significantly change?  Do I need to do something different?  BTW, the client using ubuntu 9 LTS works ok still.


I've followed the steps in this guide: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) for the client and the server.  I've attempted to reinstall the pacakges where applicable, using the --reinstall option on the apt-get command.

when I reach this line:
```

 mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/ /mnt

```

(And I fill it in with my mount points and my local directories on the client, I receive the following error message:

```

mount.nfs4: access denied by server while mounting [IpAddress]:[Exported Directory]

```

I receive the same error when attempting to mount the exported directory from the client's /etc/fstab.

The line in the /etc/fstab is:
```

IpAddress:/ExportedDirectory /mnt/Directory nfs4 rsize=8192,wsize=8192,timeo=14,intr

```

I've attempted nfs, nfs4 (both produce the same error)

Also, the server's exports file appears as such:
```

/FolderToExport ClientsIpAddress(rw,no_root_squash,async,no_subtree_check,insecure,nohide)

```

I've mucked around a bit with the options after so much google-ing, but I can't fix or make progress troubleshooting.

Any suggestions or help is very much appreciated.

---

### Post by bootedguy on 2011-05-19
Did you check the /etc/exports file on the server to make sure it was not overwritten when you upgraded?  I have a couple of 11.04 computers using NFS, and I am not aware of any changes in NFS.

---

### Post by SeijiSensei on 2011-05-19
Did you install **nfs-common** on the client?

---

### Post by RivetingScholar on 2011-05-19
What error do you get, specifically?

---

### Post by hoffman462 on 2011-05-21
Hi all,
in summary response to everyone:

I checked the /etc/exports file on the server; it is still in place.

The exact error that I am getting is:
```

mount.nfs: access denied by server while mounting 192.168.1.1:/mnt/Share

```

I guess one strange thing that I get is:
```

/dev/md0 will be checked for errors at next reboot

```
But it doesn't seem to have anything to do with nfs.  I don't know how to check the disk, and everytime i reboot the server, it never checks the disk.

The client does have nfs-common install (I ran apt-get install nfs-common).

Thanks, if you can help or suggest how to trouble shoot.

---

### Post by SeijiSensei on 2011-05-21
If /dev/md0 isn't assembled at boot, it can't be scanned.  If it can be unmounted while the server is running, run "sudo fsck /dev/md0" while it's unmounted.  If not, boot into "recovery mode", then run mount to see if the array has been assembled and mounted.  Unmount it and run fsck.

As for the NFS permissions problem, you need to look at /var/log/syslog (or perhaps /var/log/messages) on the server and see what errors it reports when you try to mount the NFS share.  What, in particular, does /etc/exports look like?  Does it have the entire subnet in the first field like this:

```
192.168.1.0/24   /export     (options)
```

Does the server have a firewall?  Does it allow TCP on port 2049?  Why are you using TCP rather than UDP?  The latter generally has better performance since the exported packets don't need to be acknowledged.

---

### Post by hoffman462 on 2011-05-21
Thanks again,
I finally was able to mount the shares on the Natty client to the Natty Server.  But not using NFSv4 (I don't have desire to use NFSv4 at all, but it seems the server and tutorials i was reading was leading me down that path).

I came across this link, with another person having this issue, with different machines:

[http://andy.delcambre.com/2007/06/25/disabling-nfsv4-on-ubuntu.html](http://andy.delcambre.com/2007/06/25/disabling-nfsv4-on-ubuntu.html)

Particularly, I added the following line to the server's /etc/default/nfs-kernel-server

```

RPCNFSDCOUNT='8 --no-nfs-version 4' 

```

The new ubuntu 11.04 client was able to mount again.

Thank you for your help.

---

