---
title: "how to seed urandom?"
date: 2010-06-13
forum: General Help
---

### Post by shellohim on 2010-06-13
How can I seed urandom (**/dev/urandom**) with numbers of my own choosing? Is it possible? Thank you.

):P

---

### Post by todak on 2010-06-13
I don't think it is possible due to urandom using noise and entropy from your machine as it boots, but if you want to generate random numbers using your own seed, then [this]("http://linux.die.net/man/3/rand") page may be of help.

---

### Post by shellohim on 2010-06-13
> **todak said:**
> I don't think it is possible due to urandom using noise and entropy from your machine as it boots, but if you want to generate random numbers using your own seed, then [this]("http://linux.die.net/man/3/rand") page may be of help.

Thanks for the reply.

Is the rand() function in c++ the same as in php? I don't want the same results I get from rand() in php. Thanks.

---

