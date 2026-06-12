---
title: "SSH without password - not working with keys"
date: 2010-12-21
forum: General Help
---

### Post by GriGGer on 2010-12-21
I have two machines at home. I am trying to setup the ssh server on the server machine so I can  connect from the client machine with no password (keys authentication).

Well, that shouldn't have been too hard, but the thing is the server user account I want to be able to connect to with keys auth has no password (that is actually the reason I want to setup keys auth). I have done everything in this guide ([http://linuxwave.blogspot.com/2007/07/ssh-without-password.html](http://linuxwave.blogspot.com/2007/07/ssh-without-password.html)), both alternatives, but with no success, because at some time I have to ssh the server to the user account that has no password (either with scp or ssh-copy-id) and it fails.

My question is: since I have root access on the server machine, can't I copy manually the public key from the client to the server? (doing manually what ssh-copy-id actually does).

Or, maybe there is another way, to change the password on the passwordless account. I have tried with # su <acct>, then passwd, but it doesn't work (asks me for the old password). I was thinking about editing /etc/shadow manually, and inserting the hash in the password field for that account (it currently has an ! ). Would that work?

Thanks,
GriGGer

---

### Post by Monotoko on 2010-12-21
you could use
```
sudo passwd <username>
```

This will change the password of any user without knowing their original password.

---

### Post by Dave_L on 2010-12-21
> **GriGGer said:**
> ... can't I copy manually the public key from the client to the server? (doing manually what ssh-copy-id actually does)

Yes. It's an ordinary text file. You can copy it anyway you like.

Actually, I think the public key needs to be appended to the file ~/.ssh/authorized_keys on the server.  That's what I had to do.

---

### Post by GriGGer on 2010-12-21
> **Dave_L said:**
> Yes. It's an ordinary text file. You can copy it anyway you like.

Yes, but where should I copy the generated public key file on the server?
EDIT: Understood, will try that, thanks!

> **Monotoko said:**
> you could use
 ```
sudo passwd <username>
```This will change the password  of any user without knowing their original password.
 
Didn't know that, will try it, thanks!

---

### Post by tredegar on 2010-12-21
> Well, that shouldn't have been too hard, but the thing is the server user account I want to be able to connect to with keys auth has no password (that is actually the reason I want to setup keys auth)
To have an account with no password is unusual.

You wouldn't be referring to the ubuntu **root** account would you? If this is the case, you might be about to make a mistake.

Best wishes.

---

