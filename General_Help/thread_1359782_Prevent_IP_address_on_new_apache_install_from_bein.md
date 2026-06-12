---
title: "Prevent IP address on new apache install from being accessed"
date: 2009-12-20
forum: General Help
---

### Post by junetwo on 2009-12-20
I have a new install of ubunutu 9.10 with apache 2.*
I've got vhosts set up for dif accounts, but if I hit the ip directly, it just flushes the directory.

I've got something like this:

# custom setup
ServerName 127.0.0.1
<Directory />
    Options MultiViews
    AllowOverride FileInfo
    Order deny,allow
    Deny from all
</Directory>
<Directory "/var/www/*">
    Allow from all
</Directory>

I assumed incorrectly that the first directory block would deny the request.. any thoughts? I could throw an htaccess file in there and shut it down?

---

### Post by junetwo on 2009-12-20
bump.

---

### Post by dcstar on 2009-12-20
> **junetwo said:**
> I have a new install of ubunutu 9.10 with apache 2.*
I've got vhosts set up for dif accounts, but if I hit the ip directly, it just flushes the directory.
.........

What does "just flushes the directory" mean?

---

### Post by junetwo on 2009-12-20
Oh I just mean it shows a directory listing of it's contents (eg. all the accounts available)

---

### Post by dcstar on 2009-12-20
> **junetwo said:**
> Oh I just mean it shows a directory listing of it's contents (eg. all the accounts available)

Which directory (exactly)?

---

### Post by junetwo on 2009-12-21
/var/www/ :(

---

### Post by junetwo on 2009-12-21
bump.

---

### Post by dcstar on 2009-12-21
> **junetwo said:**
> /var/www/ :(

The directory **you** have "Allow from all" set.

---

### Post by junetwo on 2009-12-22
<Directory "/var/www/*">
    Allow from all
</Directory>

Wildcard is in there. Is it a greedy one?

---

### Post by junetwo on 2009-12-22
Even with out, even having just this vhost setup (and nothing else, no other accounts) will still flush the directory contents when hitting the ip:

<Directory />
    Options -Indexes
    AllowOverride FileInfo
    Order deny,allow
    Deny from all
 </Directory>

---

### Post by bodhi.zazen on 2009-12-22
Use an index.html ?

Alternately see this page :

[http://httpd.apache.org/docs/1.3/misc/FAQ.html#indexes](http://httpd.apache.org/docs/1.3/misc/FAQ.html#indexes)

---

### Post by junetwo on 2009-12-22
well the first suggestion isn't really a suggestion. it's a hack more or less and my apache should be able to be configured to properly reject any requests to the ip.
the second doesn't work. i've tried it. i'm wondering if it's due to the fact that a qualified domain name isn't being requested, rather an ip so apache routes it differently?

---

### Post by junetwo on 2009-12-23
bump.

---

