---
title: "Programs Asking for Administrative Password"
date: 2012-02-01
forum: General Help
---

### Post by Muhnamana on 2012-02-01
When running a handful of programs, one in particular is the Samba program, a box appears asking for the administrative password. So I assumed it was the same password I entered when I first installed everything.

So after entering that password, it thinks a little and comes back saying invalid password. I think to myself, nope that is the correct password, caps lock is not on and retry 3 more times, no luck. I even changed my password to something simple and easy, no luck.

Anyone? I installed the server and then the desktop afterwards, wouldn't think that matters but who knows.

Suggestions? Thanks!

*EDIT
Another program that does this is KVpnc.

---

### Post by winh8r on 2012-02-07
> **Muhnamana said:**
> When running a handful of programs, one in particular is the Samba program, a box appears asking for the administrative password. So I assumed it was the same password I entered when I first installed everything.

So after entering that password, it thinks a little and comes back saying invalid password. I think to myself, nope that is the correct password, caps lock is not on and retry 3 more times, no luck. I even changed my password to something simple and easy, no luck.

Anyone? I installed the server and then the desktop afterwards, wouldn't think that matters but who knows.

Suggestions? Thanks!

*EDIT
Another program that does this is KVpnc.


Best thing to do is post which release of Ubuntu you are using and what type of server you have installed. Also a list of the programs which are causing you the problem. This will give people something to work with rather than "a handful".

If You are using a LAMP server, you will have passwords for MYSQL, phpmyadmin and for the server itself. as well as the passwords that you use on your computer for user and root.

Pencil and paper- old trick but very very reliable!!

---

### Post by SuaSwe on 2012-02-07
One way to check if your sudo password is indeed what you think it is, and that this is the password those apps are having problems with, you could try running a command in Terminal that requires this password, for example:

```

sudo fdisk -l

```

If this command does not take what you believe is your sudo password, this would suggest the password you have is not correct. :)

---

