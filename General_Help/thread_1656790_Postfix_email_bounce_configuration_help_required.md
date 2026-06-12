---
title: "Postfix email bounce configuration help required"
date: 2010-12-31
forum: General Help
---

### Post by JohnGabilochi on 2010-12-31
Hello group, I am running postfix version 2.5.5
 
[FONT=Fixedsys]home02:/etc/postfix# postconf -d | grep mail_version[/FONT]
[FONT=Fixedsys]mail_version = 2.5.5[/FONT]
[FONT=Fixedsys]milter_macro_v = $mail_name $mail_version[/FONT]
[FONT=Fixedsys]home02:/etc/postfix# [/FONT]
[FONT=Fixedsys]home02:/etc/postfix# [/FONT]
 
I have created an email black list file called bounce.txt that contains the following
 
[FONT=Fixedsys]home02:/etc/postfix#[/FONT]
[FONT=Fixedsys]home02:/etc/postfix#[/FONT]
[FONT=Fixedsys]home02:/etc/postfix# cat bounce.txt[/FONT]
[FONT=Fixedsys]#black list[/FONT]
[FONT=Fixedsys]@aspecificcompany.com REJECT[/FONT]
[FONT=Fixedsys]home02:/etc/postfix#[/FONT]
[FONT=Fixedsys]home02:/etc/postfix#[/FONT]
 
When I execute
 
[FONT=Fixedsys]postmap hash:bounce.txt[/FONT]
[FONT=Fixedsys]/etc/init.d/postfix restart[/FONT]
 
what I find is that all email from [FONT=Fixedsys]aspecificcompany.com[/FONT] doesn't reach my inbox from this company. I also find all other email from every other company or person gets through fine. Good as this is what I initially wanted, to blacklist [FONT=Fixedsys]aspecificcompany.com[/FONT].
 
What I need to do now is modify my system so that
1. all email from any user at [FONT=Fixedsys]aspecificcompany.com[/FONT] gets through only if it is sent to [EMAIL="fred@mydomain.com"][FONT=Fixedsys]fred@mydomain.com[/FONT][/EMAIL]
2. all email from any user at [FONT=Fixedsys]aspecificcompany.com[/FONT] is bounced if it is sent to any user other than[EMAIL="fred@mydomain.com"][FONT=Fixedsys]fred@mydomain.com[/FONT][/EMAIL]
 
I would appreciate some help because I don't know what I am doing.
 
Thank you 
 
John

---

