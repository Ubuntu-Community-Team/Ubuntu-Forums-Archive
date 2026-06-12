---
title: "PHP function works from Backend but not from Browser"
date: 2011-10-10
forum: General Help
---

### Post by renoy29985 on 2011-10-10
Hi Experts,

When I write a php code which includes a function like "mkdir()", it works fine when run from backend (i.e. it creates the desired directory) but when run from browser it does not.

Other php functions/code print_r work fine when called from the browser.

Please help.

Regards,
Renoy.

---

### Post by tcsmith1978 on 2011-10-10
> **renoy29985 said:**
> Hi Experts,

When I write a php code which includes a function like "mkdir()", it works fine when run from backend (i.e. it creates the desired directory) but when run from browser it does not.

Other php functions/code print_r work fine when called from the browser.

Please help.

Regards,
Renoy.

Do you mean when you call the script from a browser - it doesn't work? Are you able to check your logs?

---

### Post by renoy29985 on 2011-10-10
> **tcsmith1978 said:**
> Do you mean when you call the script from a browser - it doesn't work? Are you able to check your logs?

Yes .. when I call the script from the browser it does not create a directory. I think it is something related to permissions while creating a directory.

mmmm .. I checked the syslog but could not find anything useful. I did not post any error_log statement although .. Do you suggest me any other log ? If so, which and where shall I look for it?

I also tried to catch the exception (if any, when mkdir fails, assuming that it is failing) but nothing is thrown on the page :(

---

### Post by SeijiSensei on 2011-10-10
PHP scripts run with the same permissions as the Apache web server, namely with user and group www-data.  If you need to invoke an OS-level command like mkdir, you need to be creating the directory in a location where the www-data has write privileges.

---

### Post by renoy29985 on 2011-10-11
> **SeijiSensei said:**
> PHP scripts run with the same permissions as the Apache web server, namely with user and group www-data.  If you need to invoke an OS-level command like mkdir, you need to be creating the directory in a location where the www-data has write privileges.

Yep .. as I suspected .. that clears a way for a simple idea .. I'll implement it and let you know :) .. Tnq so much :)

---

### Post by renoy29985 on 2011-10-11
> **SeijiSensei said:**
> PHP scripts run with the same permissions as the Apache web server, namely with user and group www-data.  If you need to invoke an OS-level command like mkdir, you need to be creating the directory in a location where the www-data has write privileges.

Thank you .. It worked :)

---

