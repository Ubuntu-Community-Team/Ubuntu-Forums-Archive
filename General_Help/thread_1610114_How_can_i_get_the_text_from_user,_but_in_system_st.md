---
title: "How can i get the text from user, but in system startup stage in linux?"
date: 2010-10-31
forum: General Help
---

### Post by pitoko on 2010-10-31
Hi, sorry if i'm not writing clearly.

I want to crypt home directories using truecrypt (mount container as /home)

I know that new ubuntu support exactly that, however from some reasons i want to use truecrypt to do that.

I've place special line in fstab:
/etc/crypted_home.tc /home truecrypt

and made special script /sbin/mount.truecrypt for mounting it.

**What is the problem**: in what way can i get the password from user?
I've try different approaches, but it seems that the keyboard does not work on stage, in which the startup script is executed fstab. (i've disabled splash screen also, so i see everything what my script dumps, however i cannot enter any text).

---

