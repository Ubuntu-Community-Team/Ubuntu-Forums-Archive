---
title: "SFTP With Public Key Authentication"
date: 2011-11-21
forum: General Help
---

### Post by Holmes89 on 2011-11-21
I'm trying to set up a system that allows a specified user SFTP with public key authentication but limit that user to only have access to one folder. I've done some searching and it seems possible but could someone give me a definitive answer? I found SFTP with public key authentication [here]("http://ask-leo.com/how_can_i_automate_an_sftp_transfer_between_two_servers.html") but just not sure on how to set up the user part. Thanks!

---

### Post by azmyth on 2011-11-21
You need to setup ssh key passed authentication. Once you do this, the sftp will use the ssh transport which will be key based. Basically, you setup a key pair and add these to the host and the guest machine so once you do a sftp command it will look for a matching key pair. You can set permissions on folders to only allow access by the remote user. You can find many guides on the net on how to get ssh working with key based auth.

---

