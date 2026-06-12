---
title: "Thunderbird mail indicator icon..."
date: 2012-05-30
forum: General Help
---

### Post by timgood on 2012-05-30
I'm using Popper to inform me of new emails, so would like to remove the Thunderbird mail icon in the system tray dropdown list. In previous versions of Ubuntu you could do this by removing the file 'thunderbird' from /usr/share/indicators/messages/applications however this no longer works for very long because the file is recreated in /home/username/.config/indicators/messages/applications when Thunderbird is restarted. Placing a copy of the file in /home/username/.config/indicators/messages/application-blacklist works until Thunderbird is restarted, when the file is deleted.

So how can I remove Thunderbird from the messaging menu (I still need the indicator-messages package as Popper relies on it)? Any ideas?

---

### Post by timgood on 2012-05-30
Seems as if the new version of Thunderbird comes with an add-on called 'messaging menu and unity integration' and disabling that removes the offending behaviour.

---

### Post by ulricthered on 2012-07-07
Sorry for a naive newbie question, but please can anybody tell me  how to reset the e-mail client under the envelope drop down menu in 12.04,  to agree with my default e-mail client under "Settings" (i.e. claws). I can delete Thunderbird to remove that, but not change it to Claws.

---

### Post by ray field on 2012-11-16
I am wondering the same thing, as one of the first things I did upon installing Quantal was to unknowingly select Yahoo! Mail to be included in this indicator -- which in fact is the last thing I want because that's my garbage email account...

---

### Post by ray field on 2012-11-18
> **ray field said:**
> I am wondering the same thing, as one of the first things I did upon installing Quantal was to unknowingly select Yahoo! Mail to be included in this indicator -- which in fact is the last thing I want because that's my garbage email account...

& this morning I came across a solution: the application Unsettings lets you choose and blacklist web apps...

---

