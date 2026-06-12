---
title: "Linux SSL cert"
date: 2011-12-25
forum: General Help
---

### Post by dbwizardgirl on 2011-12-25
I received the certificate details and it works successfully on our Linux server running Apache 2 for abc.cde.company.edu.au I also tried same certificate files on our development server dev.cde.company.edu.au, and it does not work. Apache will not start with the same new certificate. (When using old certificates back apache starts and works ok). I don’t know why certificates do not work for dev.cde.company.edu.au.

---

### Post by West201 on 2011-12-25
I'm not familiar with Ubuntu servers, but I recommend you post this question in the "Server Platforms" section.

---

### Post by dcstar on 2011-12-25
> **dbwizardgirl said:**
> I received the certificate details and it works successfully on our Linux server running Apache 2 for abc.cde.company.edu.au I also tried same certificate files on our development server dev.cde.company.edu.au, and it does not work. Apache will not start with the same new certificate. (When using old certificates back apache starts and works ok). I don’t know why certificates do not work for dev.cde.company.edu.au.

Because those Certificates are probably specifically set to a website. If you want Domain wide Certificates then you should have specified that particular type.

---

