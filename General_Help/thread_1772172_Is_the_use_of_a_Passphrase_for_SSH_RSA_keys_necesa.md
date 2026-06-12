---
title: "Is the use of a Passphrase for SSH RSA keys necesary?"
date: 2011-05-31
forum: General Help
---

### Post by iclestu on 2011-05-31
what purpose does it serve to use a passphrase?

Once the keys are generated the passphrase isnt used? Or what am I missing??? I did not use a passphrase and understood that there was no security implications of not doing so. Is this correct?

---

### Post by iclestu on 2011-06-02
b-ba-baa-buuuump

---

### Post by Irihapeti on 2011-06-02
I believe that a passphrase on a key is useful if the key should get stolen.

E.g. I have a key on my EeePC. If it was stolen, there'd be nothing to stop the thief from using it if there was no passphrase.

I suppose if it's just used on a lan for a local ssh connection, it might be OK not to have a passphrase. If there's no connection possible from outside, it would seem to be of limited use to anyone.

I am willing to stand corrected if I'm wrong.

---

### Post by iclestu on 2011-06-02
> **Irihapeti said:**
> I believe that a passphrase on a key is useful if the key should get stolen.

E.g. I have a key on my EeePC. If it was stolen, there'd be nothing to stop the thief from using it if there was no passphrase.

I suppose if it's just used on a lan for a local ssh connection, it might be OK not to have a passphrase. If there's no connection possible from outside, it would seem to be of limited use to anyone.

I am willing to stand corrected if I'm wrong.

Ok, soooo - If I use my netbook to ssh into my home computer and I have set no passphrase. This doesnt make my home computer vunerable UNLESS someone gets access to my laptop to steal the key? Is this correct???

---

### Post by Irihapeti on 2011-06-02
> **iclestu said:**
> Ok, soooo - If I use my netbook to ssh into my home computer and I have set no passphrase. This doesnt make my home computer vunerable UNLESS someone gets access to my laptop to steal the key? Is this correct???

That's how I see it, yes.

The idea of having the passphrase, I understand, would be to stop them for long enough for you to disable the key.

---

### Post by CharlesA on 2011-06-02
> **Irihapeti said:**
> That's how I see it, yes.

The idea of having the passphrase, I understand, would be to stop them for long enough for you to disable the key.
Yep. It adds an extra layer of security.

That being said, you can't use keys with passphrases for stuff that would run automagically, such as an rsync backup script (that backups to to a remote machine over ssh).

---

### Post by Irihapeti on 2011-06-02
Another trick, if you don't use your key all that often, is to encrypt it. Decrypt it when you want to use it, and encrypt it again afterwards.

I do that with a passphraseless PuTTY key I have on my cellphone. Seems to work fine.

---

