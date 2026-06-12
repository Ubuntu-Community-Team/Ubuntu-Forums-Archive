---
title: "SSH keys"
date: 2011-07-18
forum: General Help
---

### Post by ROJO225531 on 2011-07-18
I just got done deploying abround 200 machines from a master image. However now I have noticed that after I conect to the new servers the ssh_host_rsa_key.pub is the same on all the machines. Can anyone tell me an easy way to generate new keys on each server?
 
Thanks

---

### Post by ajgreeny on 2011-07-18
Have you seen [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) and also [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

One of those might help, but as I seldom use ssh, I can't help in any more detail.

---

### Post by collisionystm on 2011-07-18
Try
```

ssh-keygen
```

Here is how to see the help commands

```
ssh-keygen ?
```

---

