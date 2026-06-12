---
title: "nfs-kernel-server not giving group permission"
date: 2010-09-01
forum: General Help
---

### Post by tarekeldeeb on 2010-09-01
Hello all,

I have a lab with many client PCs and 2 servers:
1- Directory server to  hold all uid/gid and other user info
2- Ubuntu Desktop 9.10 running nfs-kernel-server that exports homes. This PC server is not configured for directory server. ie. it has a single admin account. But since I export homes with no-root-squash, I can handle uids/gids from elsewhere.

This configuration worked well when the NFS was on CentOS. But not ubuntu, as the group permissions are not given.

I made sure that the server has RPCMOUNTDOPTS=--manage-gids

Can it manage the gid without being configured for the directory server?
The question can be rephrased as: when I try to access a group file, who permits me? My client who knows my groups? Or the server who doesn't?

NB: I do not what to configure the server-2 for the directory server. I dont want any non-admin client to login and load/mess with it.

Can any body give me his advice? 

Tarek

---

