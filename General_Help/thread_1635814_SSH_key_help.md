---
title: "SSH key help"
date: 2010-12-02
forum: General Help
---

### Post by t36 on 2010-12-02
Hi,

I have a question regarding the use of public/private keys and SSH. I have to be able to log in on two different servers. One server is protected by a RSA key, the other is not. 
When I log into the protected server, I am asked for the passphrase for my private key (which is what you expect). 
However, when I log into the unprotected server, I am ALSO asked for a passphrase.

I am not wondering whether this is normal behaviour, and if it isn't how I can avoid it.

Thanks in advance,

t36

---

### Post by Habitual on 2010-12-02
I generated my own ssh-key but when it came time to ask for the key pass, I just hit enter.

I never get asked for a password connecting to my server.

---

### Post by t36 on 2010-12-02
That's not the point. Why do I have to unlock the RSA key for one server when connecting to the other.

---

### Post by stlsaint on 2010-12-06
> **t36 said:**
> Hi,

I have a question regarding the use of public/private keys and SSH. I have to be able to log in on two different servers. One server is protected by a RSA key, the other is not. 
When I log into the protected server, I am asked for the passphrase for my private key (which is what you expect). 
However, when I log into the unprotected server, I am ALSO asked for a passphrase.

I am not wondering whether this is normal behaviour, and if it isn't how I can avoid it.

Thanks in advance,

t36

You say one server IS NOT using key authentication, so what does it use? Username/password?
If so then you should be entering password as you are now so im not understanding what the issue is?

---

### Post by pricetech on 2010-12-06
As suggested above, I think you're being asked for you pass "word" not passkey on the unprotected server.

---

### Post by CharlesA on 2010-12-06
If there is a private key in ~/.ssh you are prompted for the passphrase, since by default, sshd is set to use public key auth and then password auth, even if you haven't generated a keypair on the machine you are connecting to.

If I get prompted for the passphrase to my private key, I just leave it blank and hit enter, so I can move on to password auth.

---

### Post by t36 on 2010-12-07
> **CharlesA said:**
> If there is a private key in ~/.ssh you are prompted for the passphrase, since by default, sshd is set to use public key auth and then password auth, even if you haven't generated a keypair on the machine you are connecting to.

If I get prompted for the passphrase to my private key, I just leave it blank and hit enter, so I can move on to password auth.

Ah OK, this is the default behaviour. I just thought it was odd that a key belonging to one server needed to be unlocked when connecting to another server.

---

### Post by CharlesA on 2010-12-07
> **t36 said:**
> Ah OK, this is the default behaviour. I just thought it was odd that a key belonging to one server needed to be unlocked when connecting to another server.

It's not really "unlocked," it's just trying to authenticate with the current private key, which it can't do if you haven't set up the other server to do public key auth.

---

