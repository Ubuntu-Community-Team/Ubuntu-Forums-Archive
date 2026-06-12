---
title: "mySQL default character set is mixture of latin1 and utf8?"
date: 2012-04-12
forum: General Help
---

### Post by desconocido on 2012-04-12
I have, as far as I know, default installations of Ubuntu (9.10) and mySQL.

When I use phpMyAdmin and look at the "variables" page of server localhost, I see, amongst other things:

character set client utf8 (Global value) latin1
character set connection utf8 (Global value) latin1
character set database latin1
character set filesystem binary
character set results utf8 (Global value) latin1
character set server latin1
character set system utf8
character sets dir /usr/share/mysql/charsets/
collation connection utf8_general_ci (Global value) latin1_swedish_ci

This mish-mash seems to be a bit odd. Is there any useful reason for having a mixture of Latin1 and utf8?

---

