---
title: "basic fstab question"
date: 2010-12-08
forum: General Help
---

### Post by BarryDocks on 2010-12-08
I would like to mount a directory automatically for every user in their /home, please can someone tell me how to do this in fstab?

```
/home/shared/files/      /home/[COLOR="Navy"]<what goes here?>[/COLOR]/files/   none defaults,bind 0 0
```
Thanks

---

### Post by dcstar on 2010-12-08
> **BarryDocks said:**
> I would like to mount a directory automatically for every user in their /home, please can someone tell me how to do this in fstab?

```
/home/shared/files/      /home/[COLOR="Navy"]<what goes here?>[/COLOR]/files/   none defaults,bind 0 0
```
Thanks

What "goes there" is every single name of your users in an individual line for each of them.

---

### Post by BarryDocks on 2010-12-08
> **dcstar said:**
> What "goes there" is every single name of your users in an individual line for each of them.
I know it is possible to do it that way but there must be a method of using a single line to mount the directory for all users.  Possibly:
```
/home/shared/files/      /home/[COLOR="DarkSlateBlue"]~[/COLOR]/files/   none defaults,bind 0 0
```

Or
```
/home/shared/files/      /home/[COLOR="DarkSlateBlue"]$u[/COLOR]/files/   none defaults,bind 0 0
```

---

### Post by WorMzy on 2010-12-08
Nope. fstab is a configuration file which is read once, by mountall, line by line. It doesn't get looped through, and it doesn't understand variables.

---

### Post by cottfcfan on 2010-12-08
Is this tutorial helpful?

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by mcduck on 2010-12-08
Why not just symlink the directory into user homes? Since it's already a mounted filesystem I don't really see any reason to make things any more complicated than that.

You can even add the symlink in /etc/skel and it will automatcially appear for all new users you might create, so you'll only have to create the links manually for currently existing users. And even that job should be easily scriptable.

---

### Post by BarryDocks on 2010-12-08
> **mcduck said:**
> Why not just symlink the directory into user homes? Since it's already a mounted filesystem I don't really see any reason to make things any more complicated than that.

You can even add the symlink in /etc/skel and it will automatcially appear for all new users you might create, so you'll only have to create the links manually for currently existing users. And even that job should be easily scriptable.
Was trying to avoid this as I want ftp access for the users and I have disabled following symlinks in ProFTP for security.

---

