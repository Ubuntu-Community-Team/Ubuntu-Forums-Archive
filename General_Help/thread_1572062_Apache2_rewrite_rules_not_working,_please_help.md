---
title: "Apache2 rewrite rules not working, please help"
date: 2010-09-10
forum: General Help
---

### Post by nimonika on 2010-09-10
The rewrite module is enabled, the rewrite engine is on. In virtual host the AllowOverdies option is set to All. yet even the most simple rewrite is not working. Please can someone help. I do not know what more to do to debug this.

---

### Post by lisati on 2010-09-10
The first thing that comes to mind is to ask if you remembered to restart Apache after checking your settings.

---

### Post by nimonika on 2010-09-11
Yes I did indeed restart apache, the rewrite still does not work.

---

### Post by perspectoff on 2010-09-11
Not a global problem. I thought my rewrite rules weren't working today either, when the problem was actually a mis-typed symbolic link that the rewrite rule referenced.

All I can say is get a piece of licorice and try again. Aren't there Apache forums?

---

### Post by nimonika on 2010-09-11
> **perspectoff said:**
> Not a global problem. I thought my rewrite rules weren't working today either, when the problem was actually a mis-typed symbolic link that the rewrite rule referenced.

All I can say is get a piece of licorice and try again. Aren't there Apache forums?

I had breakfast actually:p and that seems to have worked as all rewrites are happening now ;). Having said that I am confused about why it worked.

Here is the background:

The files I wanted to rewrite the URI for were in the examples directory of the root folder. The .htaccess with the rules was in the root folder. I had specified the Rewrite Base in .htaccess as /examples - as I thought this to be appropriate, but nothing was working. As soon as I moved .htaccess to inside the examples directory, all rewrites were happening. I do not understand why the Rewrite base did not work- was it not supposed to work in the first place and is the .htaccess required to be in the directory where the URIs are supposed to be rewritten?

Thanks

---

