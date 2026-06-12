---
title: "I can't update 2.2.11 - 2.2.15"
date: 2010-06-07
forum: General Help
---

### Post by Morfi777 on 2010-06-07
I'm really confused....

OS: Jaunty 9.04
I have HTTPD 2.2.11 as they are in default **repos**
I tried to install 2.2.15 from **source**. I do everything as it manual but still /etc/init.d/apache2 is **2.2.11**

When I add 2.2.15 as a new init.d like here: [http://www.sucka.net/2010/04/howto-install-apache-httpd-from-source/](http://www.sucka.net/2010/04/howto-install-apache-httpd-from-source/)
Then I get like new dir (not /var/www).

Can I keep my /var/www with everything inside and just update httpd ? ...


Thanks!

---

### Post by Morfi777 on 2010-06-08
up

---

### Post by Morfi777 on 2010-06-09
bump.......

---

### Post by Morfi777 on 2010-06-09
seriously guys?!

---

### Post by lavinog on 2010-06-09
do you still have apache installed from the repositories?

what does this produce:
```

whereis apache2 apache2ctl

```
also try this:
```

/usr/sbin/apache2 -v

```

/usr/sbin/apache2 and apache2ctl should be a symlink to the binary, it likely points to the old version.

In the future, use a better title, you will likely get quicker responses.  And bumping your own thread too quickly gives the appearance that someone is already helping you.  Some users look for threads with zero replies.

---

### Post by Morfi777 on 2010-06-10
Thanks a lot for your reply!!!

When I enter [http://ip_address/asd](http://ip_address/asd) (some non existing website) I see
Apache/2.2.11 (Ubuntu) PHP/5.2.6-........

so yes, I bet this is apache2 from repos.

> root@server:~# whereis apache2 apache2ctl
apache2: /usr/sbin/apache2 /etc/apache2 /usr/lib/apache2 /usr/local/apache2 /usr/share/apache2 /usr/share/man/man8/apache2.8.gz
apache2ctl: /usr/sbin/apache2ctl /usr/share/man/man8/apache2ctl.8.gz


> root@r19317:~# /usr/sbin/apache2 -v
Server version: Apache/2.2.11 (Ubuntu)
Server built:   Mar  9 2010 21:04:15

> root@r19317:~# /usr/sbin/apache2ctl -v
Server version: Apache/2.2.11 (Ubuntu)
Server built:   Mar  9 2010 21:04:15


Both relates to 2.2.11 :/

what shall I do? :(


Cheers!

---

### Post by lavinog on 2010-06-10
You might want to uninstall the one from the repository, and recompile the new version from source.

Sometimes sticking with deb packages is nicer than compiling for this reason.

9.04 will reach end of life October 2010.  If you might want to consider upgrading to 10.04 which is a LTS (supported for 3 years or 5 years for servers.)
It will have a more recent version of apache also.

---

### Post by Morfi777 on 2010-06-10
I uninstalled apache2 once and I lol'd since website was still workin even after stopping it.

Also I would like to have 10.04 but there are 2 problems:
1. OVH (retarded company) does not offer this system yet.
2. I'm afraid that after upgrade something will mess up, also I have server 24/7 and I would not like to turn it offline. I did it once (for 4 days since OVH deleted my whole server) and I lost 160 ppl.

---

