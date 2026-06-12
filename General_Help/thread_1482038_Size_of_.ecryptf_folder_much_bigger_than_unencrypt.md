---
title: "Size of .ecryptf folder much bigger than unencrypted home"
date: 2010-05-13
forum: General Help
---

### Post by gronbaek on 2010-05-13
Hi people

I have just checked my disk usage with Baobab, and I noticed that the size of the .ecryptfs folder differs from my own user folder in /home.

I am the only user with an encrypted home, so my guess is that they should have been more or less the same size?

The .ecryptfs folder is currently at ~60GB, while my own home folder is at ~23GB. Can anybody tell me if this is to be expected? If not, what might the problem be?

---

### Post by blazemore on 2010-05-13
> **gronbaek said:**
> Hi people

I have just checked my disk usage with Baobab, and I noticed that the size of the .ecryptfs folder differs from my own user folder in /home.

I am the only user with an encrypted home, so my guess is that they should have been more or less the same size?

The .ecryptfs folder is currently at ~60GB, while my own home folder is at ~23GB. Can anybody tell me if this is to be expected? If not, what might the problem be?

Encrypted files are usually larger than their unencrypted counterparts, as the process of encryption introduces entropy, and attaches a header to each file (remember, encryptfs operates on a single-file level - I think). However, I would not expect it to be double the size.

---

