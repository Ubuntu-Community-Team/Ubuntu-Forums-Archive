---
title: "need help with .htaccess"
date: 2010-06-23
forum: General Help
---

### Post by sandyd on 2010-06-23
I really need someone to check out my url shortner .htaccess.
Apparently, it works for letters, but not for numbers. For example, [http://daura.tk/ff](http://daura.tk/ff) will work, but [http://daura.tk/4](http://daura.tk/4) will simply redirect it to the hidden URL
manually inputting it (without the shortener)  ([http://dolphinaura.com/shorturls/4](http://dolphinaura.com/shorturls/4)) works.
```

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /shorturls/
RewriteRule ^([0-9A-Za-z]+)/?$ /shorturls/yourls-go.php?id=$1 [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
</IfModule>

```

---

### Post by Leppie on 2010-06-23
apparently you're working on the site as i get some funny results when clicking the links (like the yourls install script).

---

### Post by sandyd on 2010-06-23
> **Leppie said:**
> apparently you're working on the site as i get some funny results when clicking the links (like the yourls install script).
yeah, I fixed it, turns out mod_rewrite doesn't like cloaked/shortened urls (you can't shorten a url twice lol!).

i &#9829;  yourls.org

---

### Post by Leppie on 2010-06-23
yes, i was already wondering why you were shortening twice the same link as the "long" link you posted already took me to another place.

anyways, good to hear you fixed it :)

---

