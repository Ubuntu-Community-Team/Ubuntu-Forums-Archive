---
title: "lstp client fails to login via ssh"
date: 2010-05-08
forum: General Help
---

### Post by qmax on 2010-05-08
after upgrading to 10.04 client fails to login.
after entering username/password, in ldm.log there is:

```

ssh_session: ssh -Y -t -M -S /var/run/ldm_socket_1999_10.0.0.1  -o NumberOfPasswordPrompts=1  username@10.0.0.1 echo LTSPROCKS; /bin/sh -
ldm_spawn: pid = 2430
expect saw: The authenticity of host '10.0.0.1 (10.0.0.1)' can't be established.
RSA key fingerprint is ....
Are you sure you want to continue connecting (yes/no)? 
expect saw: 
No response, restarting

```

where is that expect script?
or how could i disable adding server to known_host on client?

---

