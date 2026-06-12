---
title: "What am I missing?  Java app install woes"
date: 2009-12-14
forum: General Help
---

### Post by dlbrando on 2009-12-14
Ok, I am trying to install anyremote to get my Bberry to work as a remote, hot **** right.  Well, not yet.  Everything installed great, even on the phone, except for the java app.

I am having a hard time installing the java client on my laptop, is there a better way?

I downloaded anyremote-j2me-client-4.18.tar.gz and from ([http://sourceforge.net/projects/anyremote/files/anyremote-j2me-client/](http://sourceforge.net/projects/anyremote/files/anyremote-j2me-client/)) and extracted it. Inside I found the install text file and executed this command:

> ./configure --prefix=/usr --with-wtk=<path to WTK> --with-proguard=<path to ProGuard>
su -c "make install"

then type my password, and it returns this:

> 
su: Authentication failure

I have tried it a few times to make sure, but I get the same error. Any help?  

I would love to have this working.  I just got a bluetooth dongle for my laptop and I am working on all the cool stuff you can do.

---

### Post by bogdan.veringioiu on 2009-12-15
Hi.

Try:

```
sudo make install
```
instead of
```
su -c "make install"
```
For sudo, you can use your password.
The root account is "disabled" on ubuntu.
Cheers.
Bogdan

---

