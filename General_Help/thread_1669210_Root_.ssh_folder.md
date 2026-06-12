---
title: "Root .ssh folder"
date: 2011-01-17
forum: General Help
---

### Post by sinamorawej on 2011-01-17
Hey all

Through some mad experiment which I don't want to get into, I managed to overwrite root's .ssh folder with rsync and therefore completely disabling sudo.

Is there any hope of recovering from this situation?

Thanks
Sina

---

### Post by smurphy_it on 2011-01-17
Shouldn't be much of anything in there.  Unless you created a ssh key-pair, then it would contain your private key, public key, and potentially known_hosts files.

You may have to re-create the keypair, and place the public keys on your other servers.


ssh-keygen

---

