---
title: "id_rsa vs id_rsa.pub"
date: 2009-10-30
forum: General Help
---

### Post by zzzBrett on 2009-10-30
With ssh keys, ssh-keygen creates two files: id_rsa and id_rsa.pub.  

Is id_rsa.pub sent from the client to the server, and checked to see if it matches the authorized_keys file on the server?

If so, what does id_rsa do?

---

### Post by bribera on 2009-10-30
They're a key pair: id_rsa is your private key -- it should be kept secret, so that only you can use it; and id_rsa.pub is your public key -- you give it out so that others can verify that a given signature came from your private key. Your private key is used to sign things, and your public key is used to verify your signature.

In terms of authorized_keys and ssh, they're used like this:

1. Whoever owns the box appends the contents of your public key (id_rsa.pub) to ~/.ssh/authorized keys. This tells ssh, "if you get a request that is signed by the private key corresponding to this public key, let that request log in without a password".
2. You then initiate an ssh connection to that machine as the user whose authorized_keys contains your public key. You won't be prompted for a password, because your request will be automatically signed using your private key. ssh uses your public key to verify that the signature is valid, and allows you to log in.

You can refer to: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by zzzBrett on 2009-10-30
Thank you for the explanation.

---

