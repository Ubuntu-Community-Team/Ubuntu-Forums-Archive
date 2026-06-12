---
title: "Changed ownership prevents booting"
date: 2011-08-05
forum: General Help
---

### Post by Mahkoe on 2011-08-05
So, I've done a lot of stupid things, but this one ranks pretty high.

So I'm looking at files here and there, fooling around and tweaking things if I can, but after a while, I get sick and tired of having to fiddle around because a file's owner is root. So, completely ignoring the fact I could start an x session as root, I perform the following command:

chown -hR MY-USERNAME /

I'm thinking to myself, "Oh look at me, I'm so smart" until I turn off my laptop for the night and come back this morning, and ubuntu (10.10, 32 bit) says it could not change ICE authority (or something like that) and a few more error messages. Then, I boot into the recovery console, and again, not even bothering to think anything through properly, I chown everything back to root, then chown my home folder back to me. Anyway, I still get the error message, execpt now I can't alt-c to close the first windows that talks about the ICE authority file.

One of my friends has an ubuntu partition, so I can ask him about certain ownerships, but that could take a while and I don't know where to start. Any other options would help.

---

### Post by dinu90 on 2011-08-05
The easiest and fastest way would be to backup all your files and settings and reinstall the OS

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by coffeecat on 2011-08-05
> **dinu90 said:**
> The easiest and fastest way would be to backup all your files and settings and reinstall the OS

+1.

@Mahkoe, I'm not being unkind here but you have borked your system.

> **Mahkoe said:**
> I chown everything back to root, then chown my home folder back to me. Anyway, I still get the error message

Indeed you will. Not everything in the system folders is owned by root. There are several system processes that have their own accounts with files owned by them and not by root.

---

### Post by Mahkoe on 2011-08-05
Too bad. Okay, thanks guys

---

