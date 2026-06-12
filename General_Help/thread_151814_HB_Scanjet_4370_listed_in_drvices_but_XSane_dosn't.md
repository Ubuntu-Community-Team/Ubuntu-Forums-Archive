---
title: "HB Scanjet 4370 listed in drvices but XSane dosn't see it"
date: 2006-03-28
forum: General Help
---

### Post by j_b_seguin on 2006-03-28
Do I have to install a driver for it?
I'm quit new to Linux and Ubuntu  therefore rather lost

HHeeLp !!!!!

---

### Post by seppo on 2006-03-28
Looks like your scanner isn't supported yet:

[http://www.sane-project.org/unsupported/hp-scanjet-4370.html](http://www.sane-project.org/unsupported/hp-scanjet-4370.html)

---

### Post by j_b_seguin on 2006-03-28
I may have found a driver but how??? do I edit the file

I checked the file, the system loded a driver but with it no go

---

### Post by seppo on 2006-03-28
[quote=j_b_seguin]I may have found a driver but how??? do I edit the file

I checked the file, the system loded a driver but with it no go[/quote] 
You probably got the link [http://sourceforge.net/projects/hp3900-series/]("http://sourceforge.net/projects/hp3900-series/")

I guess you downloaded the binary and read the install instructions?


What does scanimage -L say? You should get something like: 
>  device `hp3900:libusb:005:006' is a Hewlett-Packard HP39xx Flatbed Scanner flatbed scanner 
It would be useful to check debug logging 
> hp3900 --debug 3  
It looks like at least one person got it working:
[http://sourceforge.net/forum/forum.php?thread_id=1454099&forum_id=503228]("http://sourceforge.net/forum/forum.php?thread_id=1454099&forum_id=503228")

---

### Post by j_b_seguin on 2006-03-28
I'm sorry about this but now I'm totally lost

---

### Post by seppo on 2006-03-28
[quote=j_b_seguin]I'm sorry about this but now I'm totally lost[/quote] 
Jus drop jalonsom or alvaromartinez a mail. They got it working on ubuntu:

[http://sourceforge.net/sendmessage.php?touser=1381259]("http://sourceforge.net/sendmessage.php?touser=1381259")
[http://sourceforge.net/sendmessage.php?touser=1119819]("http://sourceforge.net/sendmessage.php?touser=1119819")

I don't have a scanner and no experience with Sane so this is how far my knowledge reaches.

---

