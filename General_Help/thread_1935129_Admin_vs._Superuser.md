---
title: "Admin vs. Superuser"
date: 2012-03-03
forum: General Help
---

### Post by SergioQ on 2012-03-03
So when I installed Ubuntu, I created me, the admin.   But even I don't have writes to create in the folders /var/www.  So am assuming I need to be logged in as su.   But I never set a password for that, nor was given an option.

Yet I can do sudo to install apps.  But logged into the file directory system I obviously have very few rights.

Am confused.   The documentation is not the best here.

---

### Post by oldos2er on 2012-03-03
Use ```
sudo -i
``` to create a persistent root shell. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cwwilson721 on 2012-03-03
Personally, if I want a GUI File manager while being su, I use:
```
gksudo nautilus
```

This will give you a Nautilus window with su rights

---

### Post by snowpine on 2012-03-03
An old expression: "A little knowledge is a dangerous thing."

**Don't** use "file browser as root" (gksu nautilus) for your everyday web development purposes.

Much better to understand how Linux permissions work and set up /var/www accordingly.

A couple of resources:

[http://askubuntu.com/questions/47300/file-permissions-in-var-www-not-changing](http://askubuntu.com/questions/47300/file-permissions-in-var-www-not-changing)
[http://ubuntu-for-humans.blogspot.com/2011/04/correct-file-permissions-for-varwww.html](http://ubuntu-for-humans.blogspot.com/2011/04/correct-file-permissions-for-varwww.html)
[https://lists.ubuntu.com/archives/ubuntu-server/2009-August/003165.html](https://lists.ubuntu.com/archives/ubuntu-server/2009-August/003165.html)

---

### Post by SergioQ on 2012-03-03
Maybe am asking the wrong question then.

I thought /var/www was where the public HTML and CGI-BIN and JS files go.  But I don't have he rights to do anything there.

Am I in the wrong place or do I have to change permissions maybe?

Thanks

---

