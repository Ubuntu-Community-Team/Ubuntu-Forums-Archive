---
title: "Firefox changed font/background colour of forms - can't use Webmail anymore"
date: 2012-09-08
forum: General Help
---

### Post by calamitas on 2012-09-08
Hi there,
I use Ubuntu 10.04 LTS and Firefox 15.0. Since this morning I have a problem with Firefox:
If I'd like to use the Google search bar, the font colour of the pulldown menu, which shows some suggestions for the search, changed to a light grey and the background to white (same with the history of the address bar). However, this is not the real problem. The problem is, that I can't use the online interface of my email-provider any more (thus I'm not able to write emails with Firefox) and I'm quite sure that this is connected in some way.
Here is a picture:
[URL="http://s14.directupload.net/file/d/3007/cgxlvpwu_jpg.htm"]

If I restart Firefox in safe mode or use another profile, Firefox behaves as "usual". I tried also to delete "localstore.rdf" but it didn't have any effect (except all the settings had been changed to Firefox standard).
To be honest, I'd like to use the current profile in the future, because I would have to configure a lot, if I deleted it. 
Does anybody know how to solve this problem?

The plugins I use:
- AdBlock Plus
- Better Privacy
- BugMeNot
- Downloadhelper
- Flashgot
- Ghostery
- GreaseMonekey
- https-Finder
- Live HTTP Headers
- NoScript
- Pref Bar
- Tree Style Tab

But I've never had problems with these plugins so far.

Cala

---

### Post by vasa1 on 2012-09-08
If Firefox 15 and the combination of extensions you listed has been working for you before today, there are a couple of possibilities to consider.

Things like Adblock Plus and Ghostery get their "blocking" lists updated frequently. Maybe the NoScript one does too. An update to the lists could be the culprit.

Your profile has been corrupted.

Anyway, I don't understand why you think the "color" issue is related to accessing Webmail and how that could be.

---

### Post by calamitas on 2012-09-08
Thank you for your help. The problems were caused by Ghostery (also the color issue). I hope an update will do it.

---

