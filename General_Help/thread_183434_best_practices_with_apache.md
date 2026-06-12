---
title: "best practices with apache?"
date: 2006-05-28
forum: General Help
---

### Post by solstice on 2006-05-28
Hey everyone. I have apache2 installed w/ php4 and mySQL 4.1 currently, serving my web pages.

I know that the default web site location is /var/www. This folder my user doesn't have access to, and I was trying to come up with a way for easy development. I tried creating symbolic links from /var/www to projects in my home directory, but these can't be browsed from the web because of permission issues.

Do i have to keep my working files separate from the web files and sudo cp the changed files over the /var/www files?

How will this work when i get ftp running? I would need to create a user that has access to /var/www anyway right?

Thanks for the advice!

---

### Post by hagen00 on 2006-05-28
You can serve up files in folder other than /var/www...some claim it's even more secure to do so. 

Open up your /etc/apache2/apache.conf

and put in the following lines

```
Alias /mydir/ "/home/mydir/"
<Directory>
    Options MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>
```

Now if you type in your IP/mydir, you will get to your home folder via the web. Oh, and just remember to restart Apache once you've made those changes.

---

### Post by solstice on 2006-05-28
great thanks for the info!

---

