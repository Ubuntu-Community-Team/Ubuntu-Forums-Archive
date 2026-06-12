---
title: "Apache2 Redirect After Changing 'Document Root' from /var/www?"
date: 2010-04-02
forum: General Help
---

### Post by LurkyLou on 2010-04-02
Hi, all!
In /etc/apache2/sites-available/default, I changed my 'Document Root' and 'Directory' from /var/www to /var/www/newdir.  I have an index.php file in /var/www/newdir I use to authenticate, but when I try to redirect back to index.html in /var/www, i get a 404 error.
Anyone have info / know where the link to this discussion is?
Very much thank you! -Lou

---

### Post by e24ohm on 2010-04-02
> **LurkyLou said:**
> Hi, all!
In /etc/apache2/sites-available/default, I changed my 'Document Root' and 'Directory' from /var/www to /var/www/newdir.  I have an index.php file in /var/www/newdir I use to authenticate, but when I try to redirect back to index.html in /var/www, i get a 404 error.
Anyone have info / know where the link to this discussion is?
Very much thank you! -LouI would start with the easist items first. Did you remember to restart apache2

---

### Post by LurkyLou on 2010-04-02
Yes, restarted Apache2.
More info, using this to redirect:

<script language="javascript"><!--
location.replace("/var/www/index.html")
//-->
</script>


Also tried changing 'Allow None' statements to 'Allow All' in sites-available.

---

### Post by e24ohm on 2010-04-02
> **LurkyLou said:**
> Yes, restarted Apache2.
More info, using this to redirect:

<script language="javascript"><!--
location.replace("/var/www/index.html")
//-->
</script>


Also tried changing 'Allow None' statements to 'Allow All' in sites-available.
i'm not that strong with java scripts - I know in the past I always forget to restart apache2.

sorry i can't be of more help.

---

### Post by cdenley on 2010-04-02
> **LurkyLou said:**
> Yes, restarted Apache2.
More info, using this to redirect:

<script language="javascript"><!--
location.replace("/var/www/index.html")
//-->
</script>


Also tried changing 'Allow None' statements to 'Allow All' in sites-available.

You're trying to redirect with javascript to a local path? Are you accessing the page from the server itself? I'm not sure if that would redirect to [http://myserver/var/www/index.html](http://myserver/var/www/index.html) or to a file on the browser's local filesystem.

I just tested it. It redirects to that absolute URI, so [http://myserver/var/www/index.html](http://myserver/var/www/index.html). The server would attempt to serve /var/www/newdir/var/www/index.html which cannot be found since it doesn't exist. You cannot redirect to an html file apache isn't serving, especially with a client-side script!

---

### Post by LurkyLou on 2010-04-05
I see.  Okay, Thanks!

---

