---
title: "Email strips &quot;Return-Path&quot;"
date: 2012-10-08
forum: General Help
---

### Post by watermark on 2012-10-08
This seems like either a PHP issue or a Postfix issue, and I'd love a push in right direction.  I have complete control over the server and software.

Setup is a very basic LAMP server and Postfix.  A PHP script sends out via the "mail" function, which then hands it to Postfix.

There are a million posts out there talking about how PHP strips the "Return-Path" header due to certain security settings.  It never talks about how to disable these settings, only how to get around them with sendmail using the "-f" option.

Does anyone know how to get PHP/postfix to just leave my email alone and do as it's told?  Is using that sendmail trick the only way?

---

