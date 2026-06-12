---
title: "CHMOD settings reset?"
date: 2009-08-09
forum: General Help
---

### Post by Crath on 2009-08-09
I am trying to chmod```
/home/myname/
```to allow apache to access my www folder (for a site).

I execute the following command```
sudo chmod -r 777 myname
```and everything works fine after that.  But when I shutdown the server and start it up again, it give sme forbidden on the localhost again. It seems that it is resetting itself.

Am I doing something wrong? Thanks!

---

### Post by Monicker on 2009-08-09
Using 777 for your home directories, and all of its subdirectories, is not a very good idea.  I would recommend you use a standard public_html subdirectory for apache access. You should be able to find plenty of documentation for appropriate permissions with that setup.

As far as the permissions being reset, I do not know.   Have you checked dmesg and /var/log/messages, to see if there are any pertinent entries?

---

### Post by colau on 2009-08-15
> **Crath said:**
> I am trying to chmod```
/home/myname/
```to allow apache to access my www folder (for a site).

I execute the following command```
sudo chmod -r 777 myname
```and everything works fine after that.  But when I shutdown the server and start it up again, it give sme forbidden on the localhost again. It seems that it is resetting itself.

Am I doing something wrong? Thanks!
What happens:
```

chmod -R 777 /home/myname

```

---

