---
title: "Changing starting directory vsftpd"
date: 2009-08-19
forum: General Help
---

### Post by EmperorMoo on 2009-08-19
Hello,

I've got vsftpd running on my server, and I'd like to know how to have users be directed to /var/www/ rather than to their home directories when they log in.   My end users are all Windows users and would get quite lost...

Thanks

---

### Post by nikhilk on 2009-08-19
> **EmperorMoo said:**
> Hello,

I've got vsftpd running on my server, and I'd like to know how to have users be directed to /var/www/ rather than to their home directories when they log in.   My end users are all Windows users and would get quite lost...

Thanks

You will find all the configuration options for vsftpd [here]("http://vsftpd.beasts.org/vsftpd_conf.html")

I think local_root is the setting you are looking for. If you set local_root=/var/www, all non-anonymous logins will start in that directory but can change directories as and when required unless placed in a chroot jail.

---

### Post by EmperorMoo on 2009-08-19
That's done what I wanted!

For the record, I uncommented the chroot_local_user=YES line, and added the line

local_root=/var/www

Thanks.

---

### Post by nikhilk on 2009-08-19
> **EmperorMoo said:**
> That's done what I wanted!

For the record, I uncommented the chroot_local_user=YES line, and added the line

local_root=/var/www

Thanks.

Glad to help :)

---

