---
title: "Gtk-WARNING error when creating new virtual host - Apache2"
date: 2011-12-01
forum: General Help
---

### Post by spindler on 2011-12-01
I have installed 11.10 recently (2 weeks ago). 

I installed a number of websites and had no problems.  I recently did an update on the Ubuntu 11.10 software and now I am having issues with Apache2. 

When I create a new virtual host file  in the folder  /etc/apache2/sites-available... I get the following error.


**(Gedit: 4773) Gtk-WARNING: **: Unable to retrieve the file info for 'files:///etc/apache2/sites-available/newdev':  Error stating file '/etc/apache2/sites-available/newdev':  No such file or directory.**

Of course I just created this file and it does exist. 

The problem with this error is that after I run sudo service apache2, etc  my site does not become available.   This is really bad.

I have never had issues with apache2 creating a new virtual host before.  

WHAT DO I DO ?

Thanks

Spindler

---

### Post by darthyorik on 2011-12-10
Hi spindler,

I don't know if you've already solved this for yourself or not, but here goes.

You say you "newdev" does exist in sites-available. The site-available directly is a list of *available sites*, not *enabled sites*.

To enable your site type:

```
sudo a2ensite newdev
```

or type:

```
cd /etc/apache2/sites-enabled
sudo ln -s /etc/apahce2/sites-availabe/newdev newdev
```

to *disable* the site, at type:

```
sudo a2dissite newdev
```

or remove the symbolic link in /etc/apache2/sites-enabled/

Hope that helps, or hope that at least I've read your question correctly.

---

