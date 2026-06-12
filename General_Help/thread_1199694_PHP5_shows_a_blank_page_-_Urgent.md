---
title: "PHP5 shows a blank page - Urgent"
date: 2009-06-29
forum: General Help
---

### Post by Ravi Chandra on 2009-06-29
Hi, 

I have a project running on an old server. running on PHP4. 
I have moved files to new ubuntu machine. It shows blank page. y so?

Test page with phpinfo(); show up output and all HTML contect i.e before <?php> is hown properly. 

Pl. help me. Very urgent
Thanks,
-r

---

### Post by snek on 2009-06-29
You might want to enable error reporting, add this to the top of your page (or google on how to add it to your php.ini):

```

error_reporting(E_ALL);
ini_set('display_errors', 1);

```

Most likely it's just spitting out an error and not processing the rest of the script.
It takes quite a bit of work moving a project from PHP4 to PHP5.. It took us a good few weeks to move our websites and some we even left on an old PHP4 server.

---

