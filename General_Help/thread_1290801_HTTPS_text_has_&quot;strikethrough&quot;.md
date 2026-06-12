---
title: "HTTPS text has &quot;strikethrough&quot;"
date: 2009-10-13
forum: General Help
---

### Post by pwnst*r on 2009-10-13
but it's only in Ubuntu and only using chrome.  check the screenie.  

[IMG]http://i38.tinypic.com/10p9he8.png[/IMG]

question.  why?

---

### Post by falconindy on 2009-10-13
It's a Chrome feature when it comes across an https page with a bad cert. I'm not convinced its identifying certificates properly, but I'm too lazy to dig and find out.

---

### Post by 123456789123456789123456 on 2009-10-13
the question to ask is, is it normal?
A strike through could mean that the site is not sucure for some reason.  Or it could be a graphical symble put there by chrome to signify that it is sucured.  Have you tried googleing it?

---

### Post by pwnst*r on 2009-10-13
i wouldn't be convinced either since there's no issues on windows version of chrome.  thanks for the tip though.  prolly a beta thing.

---

### Post by pwnst*r on 2009-10-13
> **123456789123456789123456 said:**
> the question to ask is, is it normal?


why would it be normal when it doesn't display this under windows?  so linux is less secure? lol?

---

### Post by falconindy on 2009-10-13
> **pwnst*r said:**
> i wouldn't be convinced either since there's no issues on windows version of chrome.  thanks for the tip though.  prolly a beta thing.
Chromium is not Chrome.

---

### Post by pwnst*r on 2009-10-13
> **falconindy said:**
> Chromium is not Chrome.

true.

so, chromium doesn't work correctly in this case.

---

### Post by falconindy on 2009-10-14
> **pwnst*r said:**
> true.

so, chromium doesn't work correctly in this case.
That wasn't my implication at all. Chromium has features that Chrome doesn't because its the development wing and is receiving updates on a daily basis.

This is clearly a feature that doesn't (yet?) exist in Google Chrome.

---

### Post by fragos on 2009-10-14
> **falconindy said:**
> It's a Chrome feature when it comes across an https page with a bad cert. I'm not convinced its identifying certificates properly, but I'm too lazy to dig and find out.

Thanks for the explanation. I assumed it was something like that but was still very curious since I'd never seen anything like it before.

---

### Post by pwnst*r on 2009-10-14
> **falconindy said:**
> 

This is clearly a feature that doesn't (yet?) exist in Google Chrome.

i would hardly call reading security certs incorrectly a "feature".

---

### Post by falconindy on 2009-10-14
> **pwnst*r said:**
> i would hardly call reading security certs incorrectly a "feature".
Again, this is only a hunch of mine, and mostly an unfounded one. If I'm right, I'm sure other people have noticed and it'll be fixed. If I'm wrong, then there's a lot of sites who intentionally run secure http with bad certs (GMail included, which sparked my interest).

Split hairs, much?

---

### Post by falconindy on 2009-10-15
Hey look it's fixed in 4.0.222.8.

[http://code.google.com/p/chromium/issues/detail?id=24510#c3](http://code.google.com/p/chromium/issues/detail?id=24510#c3)

---

### Post by pwnst*r on 2009-10-19
> **falconindy said:**
> Hey look it's fixed in 4.0.222.8.

[http://code.google.com/p/chromium/issues/detail?id=24510#c3](http://code.google.com/p/chromium/issues/detail?id=24510#c3)

i guess my thread did some good!  and yep, confirmed here.

---

