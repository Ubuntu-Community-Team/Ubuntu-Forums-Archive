---
title: "MD5 issue"
date: 2011-06-29
forum: General Help
---

### Post by Antipacket on 2011-06-29
I downloaded *GNU coreutils* and compiled them both identically on two different computers running *Ubuntu 10.04.1 LTS*.

I performed a random audit, MD5 checking on *chown*, and they both have different checksums. Does anyone know why this has occurred?

---

### Post by mobius129a on 2011-06-29
First, try:
```
apt-cache showpkg coreutils | less
```for each to check whether they're the same version of coreutils.

---

### Post by Antipacket on 2011-06-29
Installed from source.

---

### Post by Antipacket on 2011-06-29
Bump.

---

### Post by Bachstelze on 2011-06-29
gcc probably applied different optimizations at compile time if they have different processors.

---

### Post by Antipacket on 2011-06-30
I see. What does this mean? What does it do?

Thats really bad in my opinion, because it means no ones ever going to be able to compile source and get the exact same MD5. It shouldn't be like this, as we need anti-tamper mechanism such as MD5 check.

---

### Post by Monotoko on 2011-06-30
Antipacket,

Take a look at Bochsteize signiture link, especially this part: "No amount of source-level verification or scrutiny will protect you from using untrusted code."

In order to get the same MD5 from source you need the exact same conditions, which you don't have. The only way to be 100% sure is to build your own compiler ^_^

---

