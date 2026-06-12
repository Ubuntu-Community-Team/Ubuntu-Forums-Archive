---
title: "invalid command 'AuthDigestFile'"
date: 2006-04-09
forum: General Help
---

### Post by twiggy on 2006-04-09
hey all,

i am having what seems to be a silly problem.  i am trying to set up digest on some of my folders on my website so only i have access to them.  but when i restart apache i get the following error:

Invalid command 'AuthDigestFile', perhaps miss-spelled or defined by a module not included in the server configuration

my httpd.conf file has:

<directory /var/www/mystuff/>
          Authtype Digest
          AuthName "Private"
          AuthDigestFile /usr/local/XXX/XXX/passwd
          require user jon
</Directory>

the password digest file is in the right place and set up correctly as far as i can tell.

i am really not getting why this doesnt work, i am not sure if am missing a module being loaded or have miss typed something or missed something out.

any suggestions or ideas plz guys and girls

fanks

Twiggy

---

### Post by rasti121 on 2006-09-11
I have the same problem using .htaccess:

AuthUserFile /.../htusers
AuthName "Name"
AuthType Digest
Require valid-user

Works fine with AuthType Basic, but that sents plain name/passwords over the wire, so it's rather useless.

I'm getting this erro in /var/log/apache2/error.log:

[Mon Sep 11 11:55:04 2006] [crit] [client <IP_address>] configuration error:  couldn't check user.  No user file?: /rasti

Since Basic works fine it's obviously not a file access problem.

---

### Post by asacalow on 2006-09-22
I'm having the same problem as twiggy - followed the howto here [http://www.debian-administration.org/articles/285](http://www.debian-administration.org/articles/285) to the letter but no joy.

The only difference on my setup is that I'm using an apache2.2 package from Debian's experimental feed (Yes I know).

Still, any help/ideas about where to look would be muchly appreciated!

Asa

---

### Post by derhannes on 2006-11-05
Hello,

reading [http://httpd.apache.org/docs/2.2/mod/mod_auth_digest.html](http://httpd.apache.org/docs/2.2/mod/mod_auth_digest.html) (the section on "AuthDigestProvider Directive"), I found that the mod "**authn_file**" might be necessary, too. Here's my conf:

[INDENT]           DAV On
           SSLRequireSSL
           AuthType Digest
           AuthName "webdav"
           AuthDigestProvider file
           AuthUserFile  /PATH/FILENAME
           Require valid-user[/INDENT]


Hope it may help someone

Hannes

---

### Post by farbinfarkt on 2007-05-04
I had the same problem.

I came across this blog:
[http://blog.aragirn.net/2006/11/08/debian-sarge-and-apache2/]("http://blog.aragirn.net/2006/11/08/debian-sarge-and-apache2/")

I dont know anything about apache, so i dont actually know, what I'm doing, but changing AuthDigestFile to AuthUserFile worked for me.

---

