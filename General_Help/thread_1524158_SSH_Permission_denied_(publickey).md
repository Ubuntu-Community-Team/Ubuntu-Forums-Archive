---
title: "SSH: Permission denied (publickey)"
date: 2010-07-04
forum: General Help
---

### Post by DevgruSeal on 2010-07-04
Hi, I'm having difficulties in setting up SSH pub/priv key auth. I had it working before, but it isn't now.

Here's how I started:
**~$ ssh-keygen -t rsa** - To generate a public/private key pair
**~$ cat .ssh/id_rsa.pub > .ssh/authorized_keys**

I'm connecting to this server from a Windows machine, so I transferred *id_rsa* to a folder, then imported it to puttygen.exe, and saved the private key as id_rsa.ppk -- This way I can configure PuTTY to automagically log me in.

However, when I configure PuTTY to use id_rsa.ppk as the auth file, and attempt to login, I receive *Server refused our key*. I have password auth disabled.

I tried via cmd.exe as well:
**C:\> ssh -i id_rsa user@1.2.3.4**
To which I receive:
[B]C:\> ssh -i id_rsa user@1.2.3.4
Enter passphrase for key 'id_rsa': [I do have one]
Permission denied (publickey).[/B]

---

### Post by Brandon Williams on 2010-07-07
Is it possible that you accidentally converted the key to a different type when you imported it into putty? IIRC, it doesn't require you to store the key as the same keytype when you import it.

---

### Post by bodhi.zazen on 2010-07-07
You can use ssh -vv to show additional debugging information.

Your problem could be anything from wrong permissions on the authorized_keys file to importing the wrong key to putty to using an encrypted home directory (in which case you need to store the authorized key elsewhere).

---

