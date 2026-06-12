---
title: "locate not finding stuff in home"
date: 2011-06-09
forum: General Help
---

### Post by strycat on 2011-06-09
So last year I had this problem ([http://ubuntuforums.org/showthread.php?t=1554244](http://ubuntuforums.org/showthread.php?t=1554244)) and suddenly it has started again.  

To recap in case you don't want to read the previous thread:
```

strycat@catbox:~$ locate foo

/home/.ecryptfs/strycat/.Private/ECRYPTFS_FNEK_ENCRYPTED.FXY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQI-xB3GcuqcZPLq2.6jM-gZo1raJGD.0oJBYQZdOSVPhc-/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIdV3sUJQxDIXjdd0iWhuwzE--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIRtwEDc7ZjF0EmHf3xxuPIk--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIMbk2ZszHjjdkHPAoziYGok--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQI.s4rSV9rzysxmU8jUJQ1dE--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQI1QgFBwM6KeOE.X4LM06VaU--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIS9uo-nJqhYMQvCCNZ93t2---/ECRYPTFS_FNEK_ENCRYPTED.FXY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIfUrv0eTKPQwdtyOGm41ebwEusm6HfyEdR9vVV1mJ2Zk-
/home/.ecryptfs/strycat/.Private/ECRYPTFS_FNEK_ENCRYPTED.FXY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQI-xB3GcuqcZPLq2.6jM-gZo1raJGD.0oJBYQZdOSVPhc-/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIdV3sUJQxDIXjdd0iWhuwzE--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIRtwEDc7ZjF0EmHf3xxuPIk--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQIMbk2ZszHjjdkHPAoziYGok--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRqwUQetH-Smvp7jyI65mh7bVQI.s4rSV9rzysxmU8jUJQ1dE--/ECRYPTFS_FNEK_ENCRYPTED.FWY08jC0jgRq^C

```I of course want it to return something useful like:
/home/strycat/foo
/home/strycat/foo.txt

The previous solution was to edit /etc/updatedb.conf and uncomment PRUNE_BIND_MOUNTS and remove ecryptfs from the PRUNEFS variable.

However this is my /etc/updatedb.conf
```

PRUNE_BIND_MOUNTS="yes"
# PRUNENAMES=".git .bzr .hg .svn"
PRUNEPATHS="/tmp /var/spool /media /mnt"

PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf fuse.glusterfs fuse.sshfs fusesmb devtmpfs"


```I don't know what to do at this point.  Can someone please help?

---

### Post by hakermania on 2011-06-09
You can use the 'find' command :)

---

### Post by strycat on 2011-06-09
> **hakermania said:**
> You can use the 'find' command :)

I want locate to work.  Plus find has an arcane syntax and generally takes a lot longer to return results.

---

### Post by strycat on 2011-06-13
Ok for now I think I have some kind of solution.  

I added 

PRUNENAMES=".Private"

to my /etc/updatedb.conf file.  This seem to have removed all of the encrypted nonsense.  There were also real results mixed in and impossible to see in the jumble.  So now only good results are showing and locate is working again.

---

