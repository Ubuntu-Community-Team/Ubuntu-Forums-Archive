---
title: "Chromium: allow local content to use flash/javascripts"
date: 2011-02-20
forum: General Help
---

### Post by visual1ce on 2011-02-20
I like Chrome and Chromium seems really nice on ubuntu. In Preferences -> Under the Hood -> Content Settings -> Javascript, I have selected no javascript. I then go to Exceptions to enter file:///* or similar but the input control doesn't accept this. It seems to want to a domain name and doesn't like forward slashes.

I've looked in the Preferences file but after adding a dummy exception I see no details of that exception. Anyone know where these exceptions are so I can try to manually edit?

---

### Post by kerry_s on 2011-02-20
how about 127.0.0.1, wouldn't that be the equivalent?

---

### Post by chessnerd on 2011-02-20
Chrome (and I would presume Chromium as well) stores it's configuration files in ~/.config

You are probably looking for the file ~/.config/(google-chrome or chromium)/Default/Preferences

I have no idea why Chrome/ium would act that way, but I can confirm that it does this on my system as well. You could try just using "file" but I have no idea if that would work.

Best of luck to you.

> **kerry_s said:**
> how about 127.0.0.1, wouldn't that be the equivalent?
Actually, that sounds like it might work. You could try that too.

---

### Post by visual1ce on 2011-02-20
After some fiddling I've found that there is no way to do what I am trying to do although I guess you could set a local webserver up and use 127.0.0.1. 

Chromium's exception feature is poor IMHO; whilst one can enter practically any string into the patterns section of the preferences file in /.config/Chromium/Default/ Chromium only seems to recognise domain names - no subfolders. Also, allowing plugins for blah.com will not allow plugins for [www.blah.com](www.blah.com) and visa versa.

---

### Post by kerry_s on 2011-02-20
i would check if theres a extension that does what you want, something like firefox's noscript, i think i saw a few in chromes web store.

---

