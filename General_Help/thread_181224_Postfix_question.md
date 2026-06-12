---
title: "Postfix question"
date: 2006-05-23
forum: General Help
---

### Post by horatiub on 2006-05-23
Here is my dilema: right now I have setup a mail server (Postfix) for one of my domains, but I would like to know if it's possible to setup on the same server a second mail for another domain?

So, to conclude, I wanna have the domains abc.com and xyz.com running on the same server. Is that possible?

---

### Post by horatiub on 2006-05-24
anybody?

---

### Post by seppe on 2006-05-24
You need the **Virtual Domain Hosting** feature.
You can find full documentation about it in Postfix.org pages.
Check the [Postfix Virtual Domain Hosting Howto]("http://www.postfix.org/VIRTUAL_README.html")

Maybe you can find useful these other "unofficial" howtos:

[LIST]
[*] [Virtual Users And Domains With Postfix, Courier And MySQL (+ SMTP-AUTH, Quota, SpamAssassin, ClamAV)]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier")
[*] [Virtual Users and Domains with Courier-IMAP and MySQL]("http://postfixwiki.org/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL")
[*] [Postfix virtual domain howto - Google Search]("http://www.google.com/search?q=postfix+virtual+domain+howto&btnG=Search")
[/LIST]

Don't forget to visit Flurdy's Howto on [How to set up a mail server on a GNU / Linux system (with Ubuntu)]("http://flurdy.com/docs/postfix/")

---

### Post by horatiub on 2006-05-24
I guess I'm on the right track. I have it already setup for virtual domanins with a Mysql database. Now I just need to find out how exactly to add the second domain

---

