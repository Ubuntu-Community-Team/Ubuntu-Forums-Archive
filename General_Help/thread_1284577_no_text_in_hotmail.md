---
title: "no text in hotmail"
date: 2009-10-06
forum: General Help
---

### Post by mcrene on 2009-10-06
this has been an on going problem for a couple of weeks now.
I was hoping upgrades would resolve this problem, but now its getting rather bothersome.

after upgrading to firefox 3.5 (shiretoko or something like that) a month or so ago I was unable to write emails in hotmail. the page would load, but I was never able to send anything, text would disappear when I clicked 'send'

I grew tired of this, so removed the 3.5 upgrade of firefox (shiretoko?) and went back to the current version. however the problem changed too. I was able to send a 'subject' line, but the body of text would never get to the recipient. 

so, upgraded via a "how-too" (found on here using a more stable option I was led to believe) again to firefox 3.5 but the actual mozilla release.

I am still unable to send emails. subject line will make it, but the body will not send. I have tried hotmail on my wifes Mac, on the windows boot of this laptop, at work, etc etc... but it seems this problem is centered on ubuntu on this machine.

any ideas on how to fix this problem... as I would like to be able to send emails without having to change boots, or machines everytime.

thanks for the help and support.

---

### Post by ZaHACKieL on 2009-10-06
Well I also had that problem once after an upgrade, that thing about not being able to write a msg in hotmail.

I did this:

type about:config  in the URL bar in firefox, this will show some parameters and stuff.
There you have to look for: general.useragent.vendor  , in the "value" column of that entry you may read "Ubuntu" , well, change that to:  Firefox

Restart Firefox and voila, it should work. Let me know!

ZL

---

### Post by 3rdalbum on 2009-10-06
Or you can use the User Agent Switcher add-on to tell Hotmail that you are using Firefox or Internet Explorer on Windows.

---

### Post by mcrene on 2009-10-07
> **ZaHACKieL said:**
> Well I also had that problem once after an upgrade, that thing about not being able to write a msg in hotmail.

I did this:

type about:config  in the URL bar in firefox, this will show some parameters and stuff.
There you have to look for: general.useragent.vendor  , in the "value" column of that entry you may read "Ubuntu" , well, change that to:  Firefox

Restart Firefox and voila, it should work. Let me know!

ZL



Well I tried this, but I didn't have the "general.useragent.vendor" string... so I created one with "FireFox" as its value.

WORKED. Well I sent an email to another hotmail account, and I had a subject and body. I'll try one to work and see there.

Thanks for the advice and solution.
Much appreciated.

I didn't end up trying the second post of advice since the first one worked.

---

### Post by ZaHACKieL on 2009-10-08
That's great, I'm glad! Remember to mark the thread as SOLVED =]

ZL

---

