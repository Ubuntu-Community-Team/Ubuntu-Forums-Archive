---
title: "php only works in .php files and not in .html"
date: 2011-10-08
forum: General Help
---

### Post by Snuken on 2011-10-08
Hello,
im trying to learn some php and other stuff. However, I can't get php to work unless I make a specific index.php file. If I enter <?php echo "test"; ?> for example nothing shows up.

---

### Post by SeijiSensei on 2011-10-08
That's because the Apache webserver's configuration only invokes the PHP parser when sending files ending in .php (and, I believe, the older .phtml).  You can get it to invoke PHP for .html files by using an [AddHandler]("http://httpd.apache.org/docs/2.2/mod/mod_mime.html#addhandler") directive, but that can prove problematic depending on the syntax of the HTML document.  I once added parsing of .html files, but no longer.  I just use the .php extension for PHP files, and .html for HTML-only files.

BTW, the expression <?="test"?> is a useful shorthand for <? echo "test" ?>.

---

### Post by CharlesA on 2011-10-08
> **SeijiSensei said:**
> That's because the Apache webserver's configuration only invokes the PHP parser when sending files ending in .php (and, I believe, the older .phtml).  You can get it to invoke PHP for .html files by using an [AddHandler]("http://httpd.apache.org/docs/2.2/mod/mod_mime.html#addhandler") directive, but that can prove problematic depending on the syntax of the HTML document.  I once added parsing of .html files, but no longer.  I just use the .php extension for PHP files, and .html for HTML-only files.

+1. I originally set my site up to run PHP inside HTML files, but now I just use php files, since quite a few parts are generated from php files and it's easier to keep track of things that way.

---

