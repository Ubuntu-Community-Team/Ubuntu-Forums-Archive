---
title: "Is this permission safe?"
date: 2011-04-25
forum: General Help
---

### Post by itsols on 2011-04-25
In order to create CSV files using php, I have had to give the 777 permission to my folder /var/www/Proj.

It works fine. But my question is if this is safe? If this were a public domain, wouldn't it mean that anyone visiting this folder will have RIGHT permissions to it?

Any thoughts on this would be really appreciated.

Thanks!

---

### Post by d3v1150m471c on 2011-04-25
well...if someone was able to inject code into your site then they could potentially overwrite everything in that entire tree...

---

### Post by fdrake on 2011-04-25
you can create a subfolder where you keep you CSV files and apply to it the 777 permisions. this way your root-site folder can have limited access permisions like a 755 or even less.

---

