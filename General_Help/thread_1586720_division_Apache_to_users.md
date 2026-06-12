---
title: "division Apache to users"
date: 2010-10-02
forum: General Help
---

### Post by KlMASDO444 on 2010-10-02
hello i want to division apache to users
example :if somebody going to ip/moshe/ its give to hem the page in /home/moshe/public_html
moshe is a user and i want more users

i try this:

UserDir public_html

#
# Control access to UserDir directories.  The following is an example
# for a site where these directories are restricted to read-only.
#
<Directory /home/*/public_html>
    AllowOverride FileInfo AuthConfig Limit Indexes
   Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
    <Limit GET POST OPTIONS PROPFIND>
       Order allow,deny
        Allow from all
    </Limit>
    <LimitExcept GET POST OPTIONS PROPFIND>
       Order deny,allow
        Deny from all
    </LimitExcept>
</Directory>

but its not working:(help please

---

### Post by KlMASDO444 on 2010-10-02
SomeBody here?:KS

---

### Post by KlMASDO444 on 2010-10-03
Helppppppppppppppppppp please

---

### Post by lisati on 2010-10-03
There's [virtual hosts]("http://httpd.apache.org/docs/2.0/vhosts/").

Another way might be with symbolic links, e.g. something like this:
```
ln -s /home/myuser/www/public /var/www/myuser
```

---

### Post by KlMASDO444 on 2010-10-03
> **lisati said:**
> There's [virtual hosts]("http://httpd.apache.org/docs/2.0/vhosts/").

Another way might be with symbolic links, e.g. something like this:
```
ln -s /home/myuser/www/public /var/www/myuser
```

Man The Second Option is for one user
and the first Option is for domains [www.lll.com](www.lll.com)

i want to do it on ip(this is need to be with the model userdir but i can't to it
help please!

---

