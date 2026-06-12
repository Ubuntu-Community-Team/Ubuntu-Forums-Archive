---
title: "Lost Password to encrypted partition"
date: 2011-03-10
forum: General Help
---

### Post by buntuser2 on 2011-03-10
I created a 20 GB partition using the disk utility in ubuntu 10.10 and selected "Encrypt partition" then used a password.

I am typing in the password but it looks like I must of forgot exactly how it goes.

Does anyone know how I can set a new password or recover the old password or just get the data copied to a different partition? I would think that there is a way to set a new password or recover the old password.

---

### Post by buntuser2 on 2011-03-10
argh nothing on google, just a bunch of stuff about the home directory being encrypted. Anyone had this happen before?

---

### Post by psusi on 2011-03-10
Unless you backed up the keyfile, you're forked.

---

### Post by buntuser2 on 2011-03-10
Are you sure?

There has to be a way !

---

### Post by psusi on 2011-03-10
If there was, then there wouldn't be any point to encryption in the first place would there?

---

### Post by Roguebantha on 2011-07-08
> **psusi said:**
> Unless you backed up the keyfile, you're forked.
Do you happen to know where the keyfile is?? It might be possible to hack it

---

### Post by psusi on 2011-07-08
> **Roguebantha said:**
> Do you happen to know where the keyfile is?? It might be possible to hack it

Again, if it could be hacked, that would defeat the purpose.  No password: no entry.

---

### Post by bodhi.zazen on 2011-07-08
> **Roguebantha said:**
> Do you happen to know where the keyfile is?? It might be possible to hack it

All things are possible , for example it is sometime possible to recover an encryption key via so called "cold booting", but that has a limit of a few minutes. It is possible the OP could randomly enter the password somehow too.

> **psusi said:**
> Again, if it could be hacked, that would defeat the purpose.  No password: no entry.

+1 Realistically if you lost the password or key file you are out of luck. Encryption is not designed to be trivial to crack.

---

### Post by Roguebantha on 2011-10-11
What is cold booting and how would I go about doing it?

---

### Post by Mark Phelps on 2011-10-12
> **Roguebantha said:**
> What is cold booting and how would I go about doing it?

Cold booting is exploiting the situation where information is held in memory for a few seconds even when the machine is rebooted.  It can work sometimes when the encryption key was previously in memory.

But since, you have not recently accessed the encrypted partition, it's unlikely the key will be in memory.

---

