---
title: "Firefox start error"
date: 2010-05-06
forum: General Help
---

### Post by andretav on 2010-05-06
Hi!

I upgraded to 10.04 and Firefox (3.6.3) shows this message when it starts: 

> error installing toolbar:[Exception... "Node was not found"  code: "8" nsresult: "0x80530008 (NS_ERROR_DOM_NOT_FOUND_ERR)"  location: "chrome://global/content/bindings/toolbar.xml Line: 301"]

The box message title is Javascript. 

I tried disable webfab package as this bug report suggests: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/455469](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/455469)

I removed the webfab package, but the problem remains, and I have problems running Java... Can you help me?

Thanks. 

Andre.

---

### Post by Amazing Alexander on 2010-05-15
i have the same situation too

---

### Post by Anxious Nut on 2010-06-08
same problem occurs on my netbook! The weird thing is when i copy my firefox config directory to my desktop, i dont get the error!!

edit: disabling webfab addone (tools --> addons) solved mine :)
hope it works for you all!

---

### Post by Cymrodor on 2010-07-19
Thanks for that.

---

### Post by ottabaub on 2010-08-13
> **Anxious Nut said:**
> same problem occurs on my netbook! The weird thing is when i copy my firefox config directory to my desktop, i dont get the error!!

edit: disabling webfab addone (tools --> addons) solved mine :)
hope it works for you all!

Thanks a bunch for the tip. I've been experiencing that same error for about 3 days now and it's annoying. I never used that feature so disabling it wasn't an issue.

---

### Post by Régis B. on 2010-08-17
For the record, this started occuring after I removed the webfav heart icon from the Firefox launch bar. Disabling the Webfav addon solved the issue, as recommended by Anxious Nut.

---

### Post by papaja1992 on 2010-08-17
Hi, 

Just confirming: disabling webfav solved this problem also for me. Is this problem already known to the developers of ubuntu netbook remix?

Thanks for help!

---

