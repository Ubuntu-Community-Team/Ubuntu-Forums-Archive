---
title: "Google Chromium LSO (Local stored objects / Flash Cookies) directory"
date: 2010-05-28
forum: General Help
---

### Post by sexyclient2 on 2010-05-28
Using the chromium browser beta (from a PPA in Ubuntu Tweak) I'm curious  - now that flash is "packaged" with chrome - as to whether the LSO  folder that it uses is the same (~/.macromedia) as the one Firefox uses?

I'm not too fond of LSO's at all so I block them in firefox by making  the folder read-only but I'm concerned that this (nifty little) trick  won't work for my impending switch to chromium.  I've blocked (**1)  cookies and I've blocked (**2) Javascript, but I'm a proud tinfoil  hat-wearing privacy buff and I'd like to remain as un-traceable as  possible.

**1: I can filter access to individual cookie requests for domains in  chrome, but not to a specific page  or even for a directory within a domain

**2: Javascript access filtering leaves much to be desired in chrome  because you're not allowed to filter out individual javascript requests  at all.

---

### Post by lovinglinux on 2010-05-28
I don't use Chrome, but this might help:

[https://chrome.google.com/extensions/detail/ghgabhipcejejjmhhchfonmamedcbeod](https://chrome.google.com/extensions/detail/ghgabhipcejejjmhhchfonmamedcbeod)

---

### Post by kerry_s on 2010-05-28
content settings

---

### Post by mkvnmtr on 2010-05-28
Deal with your flash cookies on the Adobe flash management page. I can not find the link but google still works. When you have the settings the way you want them they work on all the browsers you have installed. I can think of no reason to store flash cookies on my machine so I disabled it.

---

### Post by kerry_s on 2010-05-28
> **mkvnmtr said:**
> Deal with your flash cookies on the Adobe flash management page. I can not find the link but google still works. When you have the settings the way you want them they work on all the browsers you have installed. I can think of no reason to store flash cookies on my machine so I disabled it.

content settings takes you there.
some sites use cookies for passwords, for instance pandora, not a problem if you don't use sites like that.

---

### Post by sexyclient2 on 2010-05-29
Thanks guys, but for some reason I can't connect to adobe.com.  I tried pinging it but got the message 'destination host unreachable."  Surely I don't need to be on adobe.com to change these local settings?

---

### Post by sexyclient2 on 2010-06-03
I managed to access adobe.com (resolving the conflict by changing my subnet mask to something other than 255.0.0.0) and was then able to figure out that the folder ~/.macromedia is used by both firefox and chromium -- or at least the settings folder ~/.macromedia/Flash_Player/macromedia.com is.  Assuming this behavior is true for the Shared_Objects folder as well then everything is as it should be, and my original concerns were moot.  (I'll test shared objects and update if I find any unsavory behavior.)  For now, problem solved.  Thanks again.

---

