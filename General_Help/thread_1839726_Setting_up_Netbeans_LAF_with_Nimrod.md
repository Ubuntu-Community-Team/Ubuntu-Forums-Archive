---
title: "Setting up Netbeans LAF with Nimrod"
date: 2011-09-06
forum: General Help
---

### Post by sanukcm on 2011-09-06
Hi all... 

Anyone have any experience [modifying the Look and Feel of Netbeans with Nimrod]("http://personales.ya.com/nimrod/faq-en.html#10")? 

There are instructions in the link above but they are for windows it seems. 

Tried putting this in my netbeans.conf file:
```
-J-Dnimrodlf.themeFile=/home/comm/netbeans-7.0/bin/greyBlue.theme
-cp:p /home/comm/netbeans-7.0/bin/nimrodlf.jar --laf com.nilo.plaf.nimrod.NimRODLookAndFeel
```

No dice. Because there isn't specific documentation for linux and all of the third party blog posts / demos etc are for windows I am just guessing that the netbeans.conf file is where this should go but how this works is way above my head - not a java guy.

Also experimented with making some changes in Main Menu->Programming->Netbeans->Properties

No luck there either with the same code from above added to the end of the path to netbeans.

Any ideas? 

Thanks!

---

### Post by raja.genupula on 2011-09-06
[http://blogs.oracle.com/netbeansphp/entry/how_to_change_look_and](http://blogs.oracle.com/netbeansphp/entry/how_to_change_look_and)

---

