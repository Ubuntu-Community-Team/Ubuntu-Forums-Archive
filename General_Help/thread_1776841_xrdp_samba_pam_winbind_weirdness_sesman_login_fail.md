---
title: "xrdp samba pam winbind weirdness: sesman login failures despite success with tty"
date: 2011-06-06
forum: General Help
---

### Post by davious. on 2011-06-06
here is my problem: I can xrdp into my virtual server; I can winbind to my windows ads; but, I can't do both: instead I end up with sesman login failures after getting winbind going.

I'm running a couple vms through ms hyper-v; I've run into similar problems with both.

The first vm is a clone of a virtual machine that was already successfully running samba+pam+winbind. That vm was a server version of 9.10 on a 64bit platform. Because it was a 64 bit platform and the xrdp + tightvncserver has a bug on 64 bit platforms, I opted to upgrade to the 10.10 release, because xrdp doesn't need tightvncserver with that release AFAIK. So, I upgraded to 10.10, then installed xrdp. From there I successfully logged into xrdp: sesman said my network user login was successful and passed of the session to a display. It then borked because gdm wasn't installed. So, I installed ubuntu-desktop. After doing that and restarting the vm, no login works with xrdp, even local logins fail; sesman returns login failure messages. Also, when I su into a network login from a regular user, I successfully su, however, I receive the message "Erroneous Conversation (5)" after logging in.

On top of this experience, I did a fresh new vm of using the 11.04 desktop iso. After I successfully xrdped with a local account, I configured pam+samba+winbind with success: similar to my 10.10x64 experience, I could su with the "Erroneous Conversation (5)" caveat and, now, no login works with xrdp, even local logins fail; sesman returns login failure messages.

I welcome your help and guidance with regards,
Dave

---

