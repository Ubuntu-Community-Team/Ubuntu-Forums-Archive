---
title: "thunderbird does not display message body"
date: 2010-11-13
forum: General Help
---

### Post by Laszlo Ladanyi on 2010-11-13
I am running Ubuntu 10.04. for a few emails I receive thunderbird does not display the message body (header is OK). The emails where this happens are always emails where the message is there both as text/plain and as text/html as alternative. If I view the source, everything is there. I have tried to choose View->Original HTML / Simple HTML / Plain Text, but none of them worked. Any suggestions what could be the problem?

Thanks,
--Laci

---

### Post by azertyh on 2010-11-13
hello,
is "fetch headers only" in edit/account settings/server settings ticked?

---

### Post by Laszlo Ladanyi on 2010-11-13
Nope. Most email come through fine in full. Those that break always have alternative display methods in the email (text/plain and text/html). And even most of those are fine, too, but some are not... :-(

---

### Post by azertyh on 2010-11-13
find this [http://kb.mozillazine.org/Download_only_certain_POP_messages](http://kb.mozillazine.org/Download_only_certain_POP_messages)
especially about the spam detection.

---

### Post by Laszlo Ladanyi on 2010-11-13
That's a good point, but it does not apply in my case, I think. I don't have spampal/spamassassin enabled. Adaptive junk control is enabled, but these email are not marked as junk. I don't have any filters specified that would restrict to fetching the header only. In fact, my email is fetched from lotus notes, dropped into /var/spool/mail/ladanyi and thunderbird picks it up from there. The whole mail is fetched (including body) since I can look at the whole email with "view source".

---

### Post by Laszlo Ladanyi on 2010-11-13
Just some more info... Below is an email whose body is not displayed looks like. Could the empty alternatives confuse thunderbird? I suppose I could strip them with procmail... Another thing is that in the html body the <html>...</html> pair is missing as well as the <body>...</body> pair (although they are missing in other, perfectly displayed emails as well). Any suggestions?

Thanks,
--Laci

PS: azertyh, I really appreciate that you take the time to try to help. Thanks! :-)

...header...

This is a multipart message in MIME format.
--=_alternative 0065F2C9C12577D9_=
Content-Type: text/plain; charset="US-ASCII"

...body_in_plain_text...

--=_alternative 0065F2C9C12577D9_=
Content-Type: text/html; charset="US-ASCII"

...body_in_html...

--=_alternative 0065F2C9C12577D9_=--
--=_alternative
 0065F2C9C12577D9_=--
--=_alternative
 0065F2C9C12577D9_=--
--=_alternative
 0065F2C9C12577D9_=--

---

### Post by Laszlo Ladanyi on 2010-11-14
I have figured out what is wrong.

Somewhere along the way where the "bad" emails were routed the line 

"Content-Type: multipart/alternative; boundary="=_alternative 00744038882577D9_="

got broken into two lines:

"Content-Type: multipart/alternative; boundary="=_alternative 
   00744038882577D9_="

and that confused thunderbird. The question is: though thunderbird is correct, but shouldn't it try to work around this possibility?

--Laci

---

