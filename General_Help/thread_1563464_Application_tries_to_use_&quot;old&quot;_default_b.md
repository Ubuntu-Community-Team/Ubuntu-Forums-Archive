---
title: "Application tries to use &quot;old&quot; default browser"
date: 2010-08-29
forum: General Help
---

### Post by bprins on 2010-08-29
Hi,

I have an application named OpenFTD which lists spots on usenet. I have an NZB button that opens a webbrowser and opens a webpage where I can create the appropriate NZB. All great however, somehow, the web browser is misconfigured. 

When I press the button I can debug this:
```

Error showing url: Failed to execute child process "/opt/google/chrome/google-chrome" (No such file or directory)

```

Which makes sense, at some point in time, I had chrome. 

I tried:
- to reinstall openFTD and also removed all user files. Doens't change a thing.
- checked update-alternatives x-www-browser (set to opera)
- reset update-alternatives x-www-browser (firefox, just to try)
- checked udpate-alternatives gnome-www-browser (firefox)

No luck at all. 

Is there some other thing in Ubuntu that I can tweak/tune to get rid of "something" that is obviously linking to chrome.

Of course, I understand the reinstalling chrome gets rid of this issue, but I rather have it fixed.

Thanks in advance.

Bas

---

### Post by James78 on 2010-08-29
If you haven't already, you could also try changing the default browser in Gnome/KDE (see below) to the correct one.

To me, it looks like that's what could be causing the issue.

KDE:
System Settings -> Default Applications -> Web Browser -> Check "in the following browser:" radio button -> Enter "firefox"

Gnome:
```
gnome-default-applications-properties
```
Select the Custom Web browser -> Add: firefox "%s"

---

### Post by bprins on 2010-08-29
my hero,.

that did the trick. 

ashamed that the solution is so easy :)

Thanks.

Bas

---

