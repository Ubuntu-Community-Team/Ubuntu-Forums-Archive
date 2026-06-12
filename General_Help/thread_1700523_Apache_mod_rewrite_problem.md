---
title: "Apache mod_rewrite problem"
date: 2011-03-05
forum: General Help
---

### Post by DasUnk on 2011-03-05
Hello there,

I've tried to search the whole web for answers on this, and I really can't find anything of use. :( I've been trying to solve this issue now for 2 days, would be great if someone here has any idea..

When using the following RewriteRule in apache, it's not going to "?page=", it's just going to a file called "sitemap.php", so the framework is not included.
RewriteRule ^sitemap$ ?page=sitemap [L]

**When using this RewriteRule, I'm getting PHP errors:**
RewriteRule ^sitemap ?page=sitemap

**Warning**:  Unknown: failed to open stream: No such file or directory in **Unknown** on line **0**
**Warning**:  Unknown: failed to open stream: No such file or directory in **Unknown** on line **0**
**Fatal error**:  Unknown: Failed opening required 'redirect:/new/' (include_path='.:/usr/share/php:/usr/share/pear') in **Unknown** on line **0**

**The only problem for me, is that only a few of the rewrites work.. As example**
RewriteRule ^webdesign$ ?page=design [L]
RewriteRule ^recent-projects$ ?page=recentprojects [L]
RewriteRule ^about-us$ ?page=aboutus [L]
RewriteRule ^contact-us$ ?page=contactus [L]

Those works without problems, its 100% fine there..
[B]
There's a problem with:[/B]
RewriteRule ^programming$ ?page=programming [L]
RewriteRule ^copyright$ ?page=copyright [L]
RewriteRule ^sitemap$ ?page=sitemap [L]
RewriteRule ^cookies$ ?page=cookies [L]

And it doesnt help if I remove [L] or $, because it will just result in PHP error messages.

**Please note that everything works 100% fine if I change any character in the RewriteRule's.. Example:**
RewriteRule ^sitemap1$ ?page=sitemap [L]

So /sitemap1 works fine now, if I remove 1 and tries to access /sitemap it fails and only goes to the sitemap.php file.
It doesnt help to change the "?page=<pagename>", results in same problem.

**Here's the whole .htaccess file**
RewriteEngine On

#ENGLISH
RewriteRule ^programming$ ?page=programming [L]
RewriteRule ^webdesign$ ?page=design [L]
RewriteRule ^recent-projects$ ?page=recentprojects [L]
RewriteRule ^about-us$ ?page=aboutus [L]
RewriteRule ^contact-us$ ?page=contactus [L]

#SWEDISH
RewriteRule ^programmering$ ?page=programming [L]
RewriteRule ^webbdesign$ ?page=design [L]
RewriteRule ^tidigare-projekt$ ?page=recentprojects [L]
RewriteRule ^om-oss$ ?page=aboutus [L]
RewriteRule ^kontakta-oss$ ?page=contactus [L]

#OTHER
RewriteRule ^copyright$ ?page=copyright [L]
RewriteRule ^sitemap$ ?page=sitemap [L]
RewriteRule ^cookies$ ?page=cookies [L]

---------------------------------------

I'm running newest Apache2 and PHP..

Any suggestions? pleaaaaaase!

---

