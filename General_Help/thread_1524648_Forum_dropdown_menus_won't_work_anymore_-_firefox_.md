---
title: "Forum dropdown menus won't work anymore - firefox or chrome"
date: 2010-07-05
forum: General Help
---

### Post by finny388 on 2010-07-05
This appeared about 4 days ago about the same time I installed compiz.

Though when I disabled Compiz in Appearance settings, it persisted.

In Firefox 3.6.6, when I click the drowdowns e.g. Thread Tools, it expands but when I move the pointer down toward a selection, it retracts. If I don't move the pointer it will stay open.

In Chromium (5.0.375.70 (48679) Ubuntu), Thread Tools only has the first selection (Show Printable Version), no others.

I have to go to my Windows machine to mark threads Solved or Search (in new post screen).

In FF, JavaScript is enabled.

Ubuntu 10.04. wtf?

---

### Post by finny388 on 2010-07-05
Also, I installed the following FF extensions (though with Chromium misbehaving I don't know what to blame)

Shy Statusbar 1.1
Hide Menubar 3.6.201006026

---

### Post by lovinglinux on 2010-07-05
I have problems with the Thread Tools menu not working from time to time in Firefox, but it usually works after restarting the browser. I don't know the cause, but this is not a frequent problem.

I don't use Compiz. I use KDE with Kwin.

I also have noticed that while browsing a js-kit chat with Chrome, sometimes it screws up my Caps Lock functionality, mixing up uppercase letters with regular ones. The weird thing is that it also affects Firefox, if it is running when that problem happens in Chrome. So, for some reason, Chrome is messing with javascript in a way that other browsers are affected. Very weird.

Anyway, have you tried to create a new Firefox profile to see if the problem persists?

---

### Post by finny388 on 2010-07-06
New profile works like a charm.

There must be something bordering on buggy in the website code if 2 browsers had trouble for whatever reason.

Now to try and isolate the addon causing this...

thanks lovinglinux!

---

### Post by finny388 on 2010-07-06
The culprit?  - Shy Statusbar 1.1 extension.

This extensions mimics Chrome's "only show status bar when it has something to say" smart hiding.

Disable and menus work again. As for Chromium, it was a fresh install, I don't think I'll figure that one out.

Does anyone know what tool or language these forum drop downs use so that I can report this bug?

thanks

---

### Post by lovinglinux on 2010-07-06
> **finny388 said:**
> Does anyone know what tool or language these forum drop downs use so that I can report this bug?

Javascript. 

I think you should report the bug to Shy Statusbar developers.

---

### Post by finny388 on 2010-07-06
I did
thanks

---

