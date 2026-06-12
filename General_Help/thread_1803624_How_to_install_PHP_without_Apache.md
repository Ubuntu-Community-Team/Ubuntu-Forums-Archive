---
title: "How to install PHP without Apache ?"
date: 2011-07-13
forum: General Help
---

### Post by leegold on 2011-07-13
Hi,

Using Xubuntu 11.04. How do I install PHP without Apache? PHP5 in Synaptic is bundled with Apache and I'm using another server, not Apache.

Thanks,

Lee G.

---

### Post by lykwydchykyn on 2011-07-13
Depending on your web server and how you want to configure php5, I'd guess you'd need to install php5-cgi or php5-fpm.  

"php5" is just a metapackage that depends on any of a number of php5 interpreter packages, the default being apache2's mod-php5.  The two I listed above are the "standalone" options.

---

