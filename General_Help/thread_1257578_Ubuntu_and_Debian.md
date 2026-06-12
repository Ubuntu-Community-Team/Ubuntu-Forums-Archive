---
title: "Ubuntu and Debian"
date: 2009-09-04
forum: General Help
---

### Post by tushar_t on 2009-09-04
I understand from wikipedia that "Ubuntu is a fork of the Debian project's code base."

I'm looking to buy this NAS: [https://iomega-eu-en.custhelp.com/cgi-bin/iomega_eu_en.cfg/php/enduser/std_adp.php?p_faqid=20851](https://iomega-eu-en.custhelp.com/cgi-bin/iomega_eu_en.cfg/php/enduser/std_adp.php?p_faqid=20851)

The specifications say:

> **Minimum System Requirements:**

**Linux Users:**
 
[LIST]
[*]Supported Linux distributions: Redhat 9, Mandrake 10, **Debian 3.0**, Gentoo, Knoppix, Fedora Core 3 and 4 (Linux kernel 2.4.24 or above. User must have root access to the Linux System)
[*]Samba version 3.04 or above
[*]Mozilla® browser version 1.0 or above to view user's manual
[/LIST]


Does that mean it'll also run on Ubuntu 9.04?

---

### Post by R_W322 on 2009-09-04
I think, but I'm not 100% sure on this but it sounds like it will run Ubuntu 9.04 just fine I just took a look at the specs and really can't find any reason it wouldn't work for you. I believe those specs are just refereeing to the bare minimum required to use it.

RYAN.WDZIECZNY

---

### Post by Bucky Ball on 2009-09-04
> Linux kernel 2.4.24 or above

That is all you need to know.

---

### Post by tushar_t on 2009-09-04
Thanks guys. I'll go for it then.

---

### Post by Bucky Ball on 2009-09-04
To check the currently running kernel, just type:

uname -a

... in a terminal and check you are using 2.4.24 or above. It will probably look something like this:

 2.6.24-24-generic

As long as the first bit is '2.6.24' you are good to go.

---

### Post by snowpine on 2009-09-04
Debian 3.0 came out in 2002 (two years before the first Ubuntu release). No version of Ubuntu has ever used a 2.4 kernel. I think you are safe. :)

---

