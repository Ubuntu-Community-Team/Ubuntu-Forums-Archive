---
title: "Simple question about SSH keys"
date: 2012-09-13
forum: General Help
---

### Post by na5h on 2012-09-13
I'm trying to log into my Ubuntu machine using SSH with keys. I have already generated a pair of keys using ssh-keygen. Do I use the private or the public keyfile to log into my Ubuntu machine? Also, can I use the key to login using putty on a Windows machine?

---

### Post by SlugSlug on 2012-09-13
I use this guide

[http://paulkeck.com/ssh/](http://paulkeck.com/ssh/)

---

### Post by na5h on 2012-09-13
Thanks! So just to be clear: the *public *key is supposed to be on the computer from which I log into my Ubuntu system, right?

Can the public key-file be used directly with putty? I read something about having to use puttygen to create the keys for putty?

---

### Post by Lars Noodén on 2012-09-13
The public key goes into ~/.ssh/authorized_keys on the target computer, that is to say the one you are logging in to.  The private key stays on the machine your are logging in from.

As far as PuTTY goes, I haven't used it for a very long time but there is a write up here:
[http://www.howtoforge.com/ssh_key_based_logins_putty](http://www.howtoforge.com/ssh_key_based_logins_putty)

It should work with keys.

---

### Post by na5h on 2012-09-17
Ah, thanks for clearing that up for me!

---

