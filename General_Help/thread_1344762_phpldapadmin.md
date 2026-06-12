---
title: "phpldapadmin"
date: 2009-12-03
forum: General Help
---

### Post by Doin on 2009-12-03
Hi guys, 

For school we have to install phpldapadmin, and the teacher can't help with my problem.
I go to localhost/phpldapadmin, wich should be the loginscreen.
I can not log in, and get the error:
**> E_STRICT: Declaration of AJAXTree::draw_dn() should be compatible with that of PLMTree::draw_dn()**

has anyone encountered this, and if so, can anyone help me?

many thanks,

Doin

---

### Post by Doin on 2009-12-03
SOLVED:

sudo vi /usr/share/phpldapadmin/lib/AJAXTree,php
on line 16, function declaration draw_dn "$level=0" should be "$level"

---

### Post by jgoris on 2009-12-09
Nice work Doin. I had the same problem and this fixed it for me.

However, I had another issue caused by the upgrading of OpenLDAP when I upgraded Ubuntu from 9.04 to 9.10 that prevented phpldapamdin (PHA) from working. When I attempted to login to my OpenLDAP server (v2.4.18 running on Ubuntu 9.10 karmic koala) from phpldapadmin it was successful, but complained that it could not view the schema. The following message was displayed:

> 
Our attempts to find your SCHEMA for "attributetypes" have FAILEDThe PHA FAQ ([http://phpldapadmin.sourceforge.net/wiki/index.php/FAQ](http://phpldapadmin.sourceforge.net/wiki/index.php/FAQ)) has a solution for this. Also, a bug has been filed for this issue (see [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1896837.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1896837.html)) which also includes a fix, although it wasn't quite correct.

To help make this problem easier to fix for anyone else in the same boat, here is exactly what I did to fix this problem. Rather than mucking around with online config editing, the fix will edit one of the LDIF files that OpenLDAP produces and uses, presumably to load the configuration upon startup.

> sudo vi /etc/ldap/slapd.d/cn=config/olcDatabase={-1}frontend.ldifGo to the line that looks like this:

> olcAccess: to * by dn.exact=cn=localroot,cn=config manage by * breakChange the line by inserting the bold and blue text indicated below to make it look exactly like the following two lines:

> olcAccess: [COLOR=Blue]**{0}**[/COLOR]to * by dn.exact=cn=localroot,cn=config manage by * break
[COLOR=Blue]**olcAccess: {1}to dn.base="cn=subschema" by * read**[/COLOR]Restart OpenLDAP and the fix should be implemented.

> sudo service slapd restartHope this helps.

---

