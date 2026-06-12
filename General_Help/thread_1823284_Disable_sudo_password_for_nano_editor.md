---
title: "Disable sudo password for nano editor"
date: 2011-08-11
forum: General Help
---

### Post by TuxLyn on 2011-08-11
How do I disable sudo password for nano editor in my box ?

I've already tried this following line in /etc/sudoers. But I haven't logged off or rebooted the box maybe this is why it did not work.

user ALL=(ALL) NOPASSWD: /usr/bin/nano

so for example when I try to edit file /etc/nginx/nginx.conf I run
nano /etc/nginx/nfingx.conf

or this won't work because nginx.conf file belongs to root ?

Any help is appreciated. Thank you.

---

### Post by IWantFroyo on 2011-08-11
It's because that file is in your root partition.

Nano should work fine with files in your home folder.

I'm not sure what to do about that though. That's one of Ubuntu's security features.

---

### Post by TuxLyn on 2011-08-11
Yeah this is what I've figured. Thanks.

Edit, just figured out another way. This is what I did, in case any one else is interested.
root    ALL=(ALL) NOPASSWD: /usr/bin/nano, /usr/bin/gedit

---

