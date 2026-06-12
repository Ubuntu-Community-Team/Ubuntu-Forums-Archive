---
title: "Testing RewriteRule on Apache"
date: 2010-03-29
forum: General Help
---

### Post by markbusu on 2010-03-29
Hi Guys,

I have been playing around with Apache and been testing out a few things...

I have the following URL:

[www.domain.com/servlet/data?id=62](www.domain.com/servlet/data?id=62)

and wish to redirect to

[www.domain.com/servlet/1.xml](www.domain.com/servlet/1.xml)

RewriteRule /servlet/data?id=62 [http://www.domain.com/servlet/1.xml](http://www.domain.com/servlet/1.xml) [R=permanent,L]

The above does not work... I have tested a number of RewriteRule which do not include a '?' in the url, and they appear to work... The problem appears to lie with the ?...

Any tips?

I have already tried using an escape character /servlet/data\?id=62

Thanks guys!

---

