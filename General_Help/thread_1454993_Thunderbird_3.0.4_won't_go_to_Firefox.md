---
title: "Thunderbird 3.0.4 won't go to Firefox"
date: 2010-04-15
forum: General Help
---

### Post by Denton Larson on 2010-04-15
Hi everybody

I have the latest Ubuntu ver 10.04 waiting for April 29th. I have a problem with Thunderbird  3.0.4 it doesn't  get me into Firefox automatically in there is a hyper-link in the message. Anybody seen this?

Denton Larson

---

### Post by bobcollard on 2010-04-15
> **Denton Larson said:**
> Hi everybody

I have the latest Ubuntu ver 10.04 waiting for April 29th. I have a problem with Thunderbird  3.0.4 it doesn't  get me into Firefox automatically in there is a hyper-link in the message. Anybody seen this?

Denton Larson
Have you checked your Preferred Applications to see if Firefox is the preferred Browser and Thunderbird is the preferred Mail reader?

---

### Post by GAJAN on 2010-04-20
Same here, under Ubuntu 10.04, Thunderbird 3.0.4 does not direct html-links in messages to Firefox (3.6.3), that has been assigned as default browser.

---

### Post by rla on 2010-04-20
Same here - No http links in a message open a browser.

---

### Post by Ethangar on 2010-05-03
For some reason the mime handler settings didn't make it though the upgrade. I fixed it like this.
In Thunderbird click on the edit/preferences menu

Switch to attachments tab

It will likely say http under the content type and use other(?) under action. Click on that whatever it says. 

Direct it to /usr/lib/firefox-3.6.5pre/firefox

click ok and try a link again.

should work then. You may also want one for https going to the same spot.

---

