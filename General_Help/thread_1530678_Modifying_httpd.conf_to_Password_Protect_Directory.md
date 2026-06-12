---
title: "Modifying httpd.conf to Password Protect Directory"
date: 2010-07-13
forum: General Help
---

### Post by mattseanbachman on 2010-07-13
Hello:

This problem has been addressed numerous times before, but for some odd reason the steps that have solved others' problems fail to address mine.

Here's the synopsis of the issue: I can't password protect a directory I'm serving with Apache.  I'll call this directory "c".

Here's how I've modded my httpd.conf file:

```
        <Directory /var/www/c/>
                AuthType Basic
#               AllowOverride All
                AuthName "Restricted Files"
                AuthUserFile /etc/apache2/c.htpasswd
                Require user toor
        </Directory>

```The file /etc/apache2/c.htpasswd was generated with the following command:

```
 htpasswd -c /etc/apache2/c.htpasswd toor
```And I reloaded the server after this.  

This is my fifth time trying this.  I attempted to modify the location of the password file, commenting out the "AllowOverride" directive, and putting said code into the file '000-default' in /etc/apache2/sites-enabled/.

Nothing seems to work though.  

I checked the apache logs "tail /var/log/apache2/error.log" and the only thing that's in there is notices from my frequent restarts of the server as I've tried different things to fix this problem.  

The permissions of the .htpasswd file (actually the "c.htpasswd" file) are 644.  

And what's happening is that the folder is still accessible the same as it was before I tried this (i.e. no notices or whatever).  No password prompt and no notification anywhere than any checking was even attempted.

If anyone has any suggestions for me to try, let me know.  I'm pretty drained from trying to fix this myself so maybe someone with more experience or a fresh mind could see something I don't.

---

### Post by mattseanbachman on 2010-07-14
Hallelujah! 

I fixed the issue.

What apparently was happening was that I was correct with the code.  If you put the <Directory> code within /etc/apache2/httpd.conf and it's configured correctly this should work.

Save one thing: cached pages.  This was what got me.  I found out that it worked when I turned on my computer this morning to continue working on it.

The easy solution, then, is simply to clear your cache (and maybe authenticated sessions?) and then attempt it again.  

30-something people viewed this, so thanks for attempting to help, even though I didn't get any suggestions.

Marking this solved, hopefully it helps someone else in the future.

---

