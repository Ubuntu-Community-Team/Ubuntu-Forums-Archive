---
title: "NFS group permissions not working again"
date: 2010-06-10
forum: General Help
---

### Post by jlmorr on 2010-06-10
This is an old problem but seems to have shown up again.
 
I set up an NFS share on one machine. I set the permissions for the directory to 770.
 
I mount the share on another machine. If I am the owner of the directory every works fine. If I am not the owner but I am in the group that owns the directory I get a message that permission is denied.
 
I looked up the issue. The solution listed is to add the following to the file /etc/default/nfs-kernel-server
 
RPCMOUNTDOPT="--manage-gids"
 
This line is already in the file. I have restarted the service and the server. gids and uids are identical on the machines.
 
I am running 10.04 LTS.
 
Is anybody else having this problem. I did not have the problem with jaunty.

---

### Post by jlmorr on 2010-06-14
I found out that the group permissions are working. It just doesn't work for one account. Why it doesn't work for that one account is a mystery. The user is a member of 3 groups so there shouldn't be a problem there. Other users are in more accounts. The uids and gids are identical on the machines. I've decided to give up and not worry about it because the account is for testing purposes only.

---

### Post by jlmorr on 2010-06-14
I fixed the problem. I looked at the accounts on both machines. The usernames were the same but the real names were different. Changing the real names to agree fixed the problem.

---

