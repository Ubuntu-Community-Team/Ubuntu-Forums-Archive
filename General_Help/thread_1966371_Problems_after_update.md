---
title: "Problems after update"
date: 2012-04-27
forum: General Help
---

### Post by Tex-Twil on 2012-04-27
Hi,
yesterday I get a notification in my Kubutu that I have some updates available so I did them. After rebooting I have the following issues:

Problem 1: boot takes ages! The boot sequence stays around 3 minutes on this message: "Starting CUPS printing spooler/server"


Problem 2: the NFS mounts do not work anymore:
```


sudo mount /home/me/REMOTE                                                                                                                                      
mount.nfs: rpc.statd is not running but is required for remote locking.                                                                                                            
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.                                                                                                             
mount.nfs: an incorrect mount option was specified


```

My fstab entry looks like this:
```

192.168.0.1:/home/me                             /home/me/REMOTE nfs  rw,noauto,soft,intr,addr=192.168.0.1  0 0

```


Edit Problem 2: it works if I start "/etc/init.d/statd start". Is this normal ? Should it be starting automatically at boot ??

Any ideas ?

I wish some day updating a Linux system doesn't mean breaking up the system :(

---

