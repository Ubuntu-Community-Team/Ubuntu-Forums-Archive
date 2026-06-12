---
title: "Intalling app in language different from locale"
date: 2009-11-30
forum: General Help
---

### Post by s2n6 on 2009-11-30
Dear all,

My karmic installation is in English. However, I want to install one application in a different language (Dutch). Is there a simple apt-get based way to to this?

grtz

---

### Post by Leppie on 2009-11-30
Not sure about only one application. However if you go to System>Administration>Language Support you can add languages and have all applications that support the language updated for that language.

---

### Post by VCoolio on 2009-11-30
Make sure you have both english and dutch language support (see the post above), then run the application you want in Dutch like this (make a launcher or edit the application menu entry):

LANGUAGE=nl application-command

---

### Post by Leppie on 2009-11-30
A bit ot, but...
Are there a lot of Dutch users in this forum (I'm one...)?

---

### Post by s2n6 on 2009-12-02
thx for the tips. It worked.

s2n6

---

