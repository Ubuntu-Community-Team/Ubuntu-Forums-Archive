---
title: "Command Line Mail Client Server"
date: 2011-01-27
forum: General Help
---

### Post by whitelinux on 2011-01-27
I have just got myself up and running on a ubuntu 32 bit server with postfix using this guide here [http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3) and everything is working great ( i didnt install ispconfig )

I want to get a command line mail client running but I am having some permission issue.


sudo aptitude install heirloom-mailx

then when i type mail this happens

mail
/var/mail/jj: Permission denied

i also tried mutt etc but always get permission denied.

Anyone know how i proceed?

thanks :}


drwxr-xr-x 6 jj   jj        4096 2011-01-27 09:37 Maildir/

---

### Post by gmargo on 2011-01-27
So what are the permissions in /var/mail?

```

$ ls -la /var/mail
total 16
drwxrwsr-x  2 root   mail 4096 Jan 19 07:53 .
drwxr-xr-x 14 root   root 4096 Dec  8 10:40 ..
-rw-rw----  1 gmargo mail 3970 Jan 19 07:53 gmargo
-rw-rw----  1 nobody mail 2547 Dec 26 08:00 nobody

```

---

### Post by whitelinux on 2011-01-27
$ ls -la /var/mail
total 8
drwxrwsr-x  2 root mail 4096 2011-01-27 19:00 .
drwxr-xr-x 14 root root 4096 2011-01-27 08:24 ..
-rw-------  1 root mail    0 2011-01-27 19:00 jj

btw i am running postfix i edited what i wrote incorrectly above

---

### Post by gmargo on 2011-01-27
> **whitelinux said:**
> 
```

$ ls -la /var/mail
total 8
drwxrwsr-x  2 root mail 4096 2011-01-27 19:00 .
drwxr-xr-x 14 root root 4096 2011-01-27 08:24 ..
-rw-------  1 root mail    0 2011-01-27 19:00 jj

```btw i am running postfix i edited what i wrote incorrectly above

The permissions are wrong for the 'jj' file.  It should be owned by jj and 660.  Fix it with:
```

$ sudo chown jj /var/mail/jj
$ chmod 660 /var/mail/jj

```Then the mail command should work. (Of course, it's zero length so there is no content.)

---

### Post by Habitual on 2011-01-27
* sudo touch /var/mail/jj
    * sudo chown jj:mail /var/mail/jj

---

### Post by whitelinux on 2011-01-28
THank you for sorting that out!

Worked perfectly :P

---

### Post by Habitual on 2011-01-28
JJ:

Us JJs have to stick together. :KS

Glad it worked out.

---

