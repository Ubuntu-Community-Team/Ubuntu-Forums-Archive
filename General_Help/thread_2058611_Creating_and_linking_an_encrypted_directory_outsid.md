---
title: "Creating and linking an encrypted directory outside of home"
date: 2012-09-16
forum: General Help
---

### Post by pteri498 on 2012-09-16
Question: Can I create an encrypted directory with ecryptfs that exists outside of my home directory, which uses the same decryption credentials that my encrypted home directory uses?

Here's the situation:
```
/dev/sda1 (SSD): /
/dev/sdb1 (HDD): /home
/dev/sdb2 (HDD): /var and /tmp
```

The above works fine, but I have 80GB free on /dev/sda1 that I'd like accessible from my home directory.

My home directory is encrypted with ecryptfs. I'd like the new directory on /dev/sda1 to do the same thing. I created the following, which I want to link from my home directory:

```
/home_ext/username on /dev/sda1
```

Then if I try to encrypt it:

```
/home_ext/username $ ecryptfs-setup-private 
ERROR:  wrapped-passphrase file already exists, use --force to overwrite.
```

I see from the manpage that ecryptfs puts a lot of important files in the home directory. I'd like to get some advice if I'm going about this the right way.

---

