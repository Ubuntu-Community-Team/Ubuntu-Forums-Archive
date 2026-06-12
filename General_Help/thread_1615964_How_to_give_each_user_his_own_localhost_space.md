---
title: "How to give each user his own localhost space?"
date: 2010-11-07
forum: General Help
---

### Post by Isamtron on 2010-11-07
Hello,

I installed Apache2/PHP/MySQL on 10.10. Everything seems fine apart from being confused about how to give each Desktop User his own localhost space.

What I mean is the machine will be used by more than one PHP developer so the files should be placed in /home/user/webdev instead of the default location (/var/www/)

How could I do that? That's one.

The second thing I'm wondering about is, will I be able to let each user access the localhost through [http://localhost](http://localhost) only or it MUST be [http://localhost/~user/](http://localhost/~user/)

Please help. Thanks.

---

### Post by lykwydchykyn on 2010-11-07
The simple way to do it is to enable the "userdir" module for apache.  This publishes anything under ~/public_html to [http://localhost/~username/](http://localhost/~username/).

The command is:
```

sudo a2enmod userdir
sudo apache2ctl restart

```

You can change the ~/public_html part to another directory, but I'm not sure if there is a way to change the ~ thing to something else.  You might want to check the manual on that one: [http://httpd.apache.org/docs/2.0/mod/mod_userdir.html](http://httpd.apache.org/docs/2.0/mod/mod_userdir.html)

If there aren't a lot of users, and they don't change much, it may be simpler to just create symlinks from each user's home directory to /var/www.  Like this:
```

sudo ln -s /home/user/somedirectory /var/www/user

```

Personally, I've had a lot of odd issues with the userdir module and scripts or .htaccess directives, so I just go with the symlink method now.

---

### Post by Isamtron on 2010-11-08
[REMOVED]

Sorry, after rereading what you said I was able to use both methods.

Thanks so much.

---

### Post by WorMzy on 2010-11-08
Have you created the "public_html" folder in your home directory?

Also, I trust you're replacing "username" in the URL with your username? e.g.

[http://localhost/~isamtron]("http://localhost/~isamtron")

EDIT: Nevermind. :)

---

### Post by Isamtron on 2010-11-08
Thanks WorMzy and sorry for the delay in editing my post but I really edited it as soon as it worked for me.

---

