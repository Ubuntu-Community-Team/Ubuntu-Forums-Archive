---
title: "Help required with GPG"
date: 2012-04-26
forum: General Help
---

### Post by flurospar on 2012-04-26
Looking for ways to encrypt mail, I came across GPG, and I was able to set it up without problems. However, I read somewhere that it's good to have keys that expire, and hence I set up a key that expires in 5 years.

Now, my question is, what happens after the key expires? I am clueless to this part and can't figure it out.

Please help and many thanks in advance.

---

### Post by codemaniac on 2012-04-26
A key's expiration time is associated with the key's self-signature. The expiration time is updated by deleting the old self-signature and adding a new self-signature.

---

### Post by flurospar on 2012-04-26
> **codemaniac said:**
> The expiration time is updated by deleting the old self-signature and adding a new self-signature.

Can anyone please explain this, and most importantly, how to accomplish this?

(I have installed Enigmail on Thunderbird and along with it Kleopatra.)

---

### Post by codemaniac on 2012-04-26
Signing public key components with the corresponding private master signing key is called self-signing .
Here is a good documentation for you .
[http://www.gnupg.org/gph/en/manual.html](http://www.gnupg.org/gph/en/manual.html)

---

### Post by flurospar on 2012-04-26
Many thanks, I got it now.

I have to simply update the expiration time when the key nears expiration.

---

