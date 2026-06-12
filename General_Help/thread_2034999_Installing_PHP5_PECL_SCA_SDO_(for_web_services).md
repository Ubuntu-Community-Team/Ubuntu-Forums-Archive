---
title: "Installing PHP5 PECL SCA_SDO (for web services)"
date: 2012-07-29
forum: General Help
---

### Post by dragonfly41 on 2012-07-29
I'm trying to install PHP5 PECL extension SCA_SDO

[http://uk3.php.net/manual/en/sdo.installation.php](http://uk3.php.net/manual/en/sdo.installation.php)

Building SDO in Linux

I get as far as **[COLOR=Blue]phpize[/COLOR]** then **[COLOR=Blue]./configure[/COLOR]**

but I then get this message

[COLOR=Blue]**configure: error: xml2-config not found. Please check your libxml2 installation.**[/COLOR]

Looking at Synaptic Package Manager I do have libxml2 installed.
libxml2 2.7.7dfsg-4ubuntu

Any ideas on how to progress beyond this stage to build the extension sdo.so?

............

More background reading on SCA_SDO here ..

[http://www.php.net/manual/en/sca.examples.exposing-webservice.php](http://www.php.net/manual/en/sca.examples.exposing-webservice.php)

[http://www.ibm.com/developerworks/web/library/ws-soa-scasdo/](http://www.ibm.com/developerworks/web/library/ws-soa-scasdo/)

[http://www.ibm.com/developerworks/webservices/library/ws-soa-scasdo/](http://www.ibm.com/developerworks/webservices/library/ws-soa-scasdo/)

.............

[COLOR=DarkRed][Edit]

Since posting I've found that I need to also install libxml2-dev package.[/COLOR] [COLOR=DarkRed]

I've now progressed a bit further down the build chain.[/COLOR] [COLOR=DarkRed]

I'm now seeing this ..[/COLOR] [COLOR=DarkRed]

libtool: compile: Failed to create `.libs'[/COLOR]

---

### Post by dragonfly41 on 2012-07-30
I've since found out by searching around that major changes are needed to compile SCA_SDO on PHP 5.3

read here ..

[https://groups.google.com/forum/?fromgroups#!topic/phpsoa/764anp-RwKA](https://groups.google.com/forum/?fromgroups#!topic/phpsoa/764anp-RwKA)

[http://www.mail-archive.com/phpsoa@googlegroups.com/msg00813.html](http://www.mail-archive.com/phpsoa@googlegroups.com/msg00813.html)

---

### Post by dragonfly41 on 2012-07-30
I've now used the SDO fork here for PHP 5.3

[https://github.com/CloCkWeRX/sdo](https://github.com/CloCkWeRX/sdo)

which compiles to completion without errors.

Thanks to CloCkWeRX.

---

