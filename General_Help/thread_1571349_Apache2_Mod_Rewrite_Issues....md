---
title: "Apache2 Mod_Rewrite Issues..."
date: 2010-09-09
forum: General Help
---

### Post by thezwallrus on 2010-09-09
goodday,

I've given a bit of support using Mod_rewrite to use magical urls to redirect to scripts, but when I migrated to Ubuntu's Apache2... I'm lost. I basically want to rewrite like this:

```
RewriteRule ^artist/(.+)/$ artist.php?artname=$1
```

But I noticed that it wasn't passing the artist=$1 to the server GET vars. Then I noticed that if I changed the name of the file in both the rule and the file system to **artists.php**, typing artist/blah/ no longer was found. So then I realized that if I removed the rewrite rule artist/hello/ would still resolve to artist.php without any parameters

my htaccess is like so:

```
Options +FollowSymLinks

RewriteEngine on
RewriteBase /
RewriteRule ^artist/(.+)/?$ artists.php?artist=$1
```

why is it automagically resolving everything past artist to artist.php?! i'm lost.

---

### Post by gabehamilton on 2010-09-23
The issue I had was that I had Options MultiViews in my virtual host config (/etc/apache2/sites-available/default).  MultiViews was essentially rewriting the url before mod_rewrite.
See [http://serverfault.com/questions/60/mod-rewrite-does-not-forward-get-parameters](http://serverfault.com/questions/60/mod-rewrite-does-not-forward-get-parameters) for a full explanation.

---

