---
title: "Possible flash help"
date: 2012-08-13
forum: General Help
---

### Post by etphoto on 2012-08-13
When attempting to log into certain flash chat sites I get the following message.
 
[IMG]http://i1253.photobucket.com/albums/hh591/etphotography/Screenshotfrom2012-08-1313_27_59.png[/IMG]
 
I use to be able to just click the close button and go into the chat site. But I reinstalled 12.04 (to fix another issue) and now I click and click and nothing happens. Its as if the close button is grayed out (which it isn't). My flash and system is updated. It happens no matter what browser I'm using. Any help?

---

### Post by etphoto on 2012-10-30
Bump

No ideas?

---

### Post by hal8000 on 2012-10-30
Try reinstalling the flashplugin

sudo apt-get install flashplugin


Install google chrome to see if its briwser related or just happens on firefox, I would quote the URL of the site you use to see if anyone else has same problem.

---

### Post by COMECON on 2012-10-30
Have you tried Google Chrome (not Chromium)? It ships with its own flash plugin.

---

### Post by etphoto on 2012-10-31
> **COMECON said:**
> Have you tried Google Chrome (not Chromium)? It ships with its own flash plugin.

No I have not.  I've been using Chromium. Let me investigate.

btw, it happens with either Firefox and Chromium and it never happened before I re-installed 12.04.

---

### Post by COMECON on 2012-10-31
> **etphoto said:**
> No I have not.  I've been using Chromium. Let me investigate.

btw, it happens with either Firefox and Chromium and it never happened before I re-installed 12.04.

Additionaly, you could try installing *ubuntu-restricted-extras*. It may help.

---

### Post by dentaku65 on 2012-10-31
> **etphoto said:**
> When attempting to log into certain flash chat sites I get the following message.
 
[IMG]http://i1253.photobucket.com/albums/hh591/etphotography/Screenshotfrom2012-08-1313_27_59.png[/IMG]
 
I use to be able to just click the close button and go into the chat site. But I reinstalled 12.04 (to fix another issue) and now I click and click and nothing happens. Its as if the close button is grayed out (which it isn't). My flash and system is updated. It happens no matter what browser I'm using. Any help?

Are you able to expand in full screen the flash chat box? If yes, in full screen you'll be able to use the close button of window flash.

by

---

### Post by etphoto on 2012-10-31
> **COMECON said:**
> Additionaly, you could try installing *ubuntu-restricted-extras*. It may help.

That didn't work but installing Google Chrome did.  Its apparently a plugin issues since Chrome works and firefox and chromium didn't.

---

### Post by COMECON on 2012-10-31
You could try uninstalling the flash plugin, and maybe having only Chrome's plugin will fix the problem.

---

### Post by etphoto on 2012-11-12
This is EXACTLY my problem and a fix.  I found it on accident. :)

[http://www.youtube.com/watch?v=ZWJu4QbzJBo](http://www.youtube.com/watch?v=ZWJu4QbzJBo)

---

