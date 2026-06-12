---
title: "Delay when logging in"
date: 2009-09-20
forum: General Help
---

### Post by craigmcfly on 2009-09-20
I've just installed Jaunty Server 32-bit on a VIA CPU (Epia motherboard) and whether I log in over ssh or directly onto console I get an absurdly long delay before it brings up a prompt. 

When I log in over ssh, I get the following in the auth.log

Sep 20 16:40:52 epia sshd[18475]: pam_sm_authenticate: Called 
Sep 20 16:40:52 epia sshd[18475]: pam_sm_authenticate: username = [craig] 
Sep 20 16:40:52 epia sshd[18475]: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Sep 20 16:41:22 epia sshd[18474]: Passphrase key already in keyring; rc = [1] 
Sep 20 16:41:22 epia sshd[18474]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [15c10b1722385a7b] to the keyring; rc = [1] 
Sep 20 16:41:22 epia sshd[18474]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Sep 20 16:41:30 epia sshd[18477]: Passphrase key already in keyring; rc = [1] 
Sep 20 16:41:30 epia sshd[18477]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [15c10b1722385a7b] to the keyring; rc = [1] 
Sep 20 16:41:30 epia sshd[18477]: Error attempting to add filename encryption key to user session keyring; rc = [1] 
Sep 20 16:41:40 epia sshd[18474]: Passphrase key already in keyring; rc = [1] 
Sep 20 16:41:41 epia sshd[18474]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [50276cfb7ddce23b] to the keyring; rc = [1] 
Sep 20 16:41:41 epia sshd[18474]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Sep 20 16:41:41 epia sshd[18474]: There is already a key in the user session keyring for the given passphrase. 
Sep 20 16:41:41 epia sshd[18472]: Accepted password for craig from 192.168.1.3 port 53411 ssh2
Sep 20 16:41:41 epia sshd[18472]: pam_unix(sshd:session): session opened for user craig by (uid=0)
Sep 20 16:41:41 epia sshd[18472]: Mount of private directory return code [0]
Sep 20 16:41:41 epia sshd[18472]: pam_unix(sshd:session): session closed for user craig
Sep 20 16:41:41 epia sshd[18472]: Mount of private directory return code [0]
Sep 20 16:41:45 epia sshd[18477]: Passphrase key already in keyring; rc = [1] 
Sep 20 16:41:45 epia sshd[18477]: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [50276cfb7ddce23b] to the keyring; rc = [1] 
Sep 20 16:41:45 epia sshd[18477]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Sep 20 16:41:45 epia sshd[18477]: There is already a key in the user session keyring for the given passphrase. 
Sep 20 16:41:45 epia sshd[18475]: Accepted password for craig from 192.168.1.3 port 53412 ssh2
Sep 20 16:41:45 epia sshd[18475]: pam_unix(sshd:session): session opened for user craig by (uid=0)
Sep 20 16:41:46 epia sshd[18475]: Mount of private directory return code [0]


My home directory has encryption enabled (set up during the install process).

Any info is welcome. 

Cheers,

Craig

---

### Post by ubudog on 2009-09-20
Might be the encryption, but I'm not an expert.

---

### Post by kindofabuzz on 2009-11-07
I have the same problem. But did not have this problem with 9.04 server. But on the 9.04 server I did not have /home encrypted. The above post said encryption could be a factor?

---

