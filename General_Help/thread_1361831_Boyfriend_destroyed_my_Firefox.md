---
title: "Boyfriend destroyed my Firefox"
date: 2009-12-22
forum: General Help
---

### Post by kyate on 2009-12-22
I let my boyfriend use my laptop and now Firefox will not open for me. There is no homepage for it connect to and thus when I click to open Mozilla the opening icon goes but then just stops. The window appears on the taskbar but then disappears. What did he do and what can I do to undo it?

---

### Post by ibuclaw on 2009-12-22
Try renaming the Firefox user directory to "**.mozilla.old**" and try again.

via commandline, that is:
```
mv ~/.mozilla ~/.mozilla.old
```

Regards
Iain

---

### Post by houseworkshy on 2009-12-22
Alternatively use synaptic package manager to completely remove firefox and then reinstall it.

---

### Post by Shpongle on 2009-12-22
did he install any add ons or mess with connection settings?

if nothing else works you could try delete your .mozilla folder in your home directory , this stores ff's config as well as thunderbird's , it'll  delete your themes and extensions etc. basically it will be like a new firefox. be aware that thunderbirds settings will also be deleted if you do this . next time you run them the folders will be automatically created.

---

### Post by kyate on 2009-12-22
> **tinivole said:**
> Try renaming the Firefox user directory to "**.mozilla.old**" and try again.

via commandline, that is:
```
mv ~/.mozilla ~/.mozilla.old
```Regards
Iain

I tried it exactly and it says no such file exists.

---

### Post by kyate on 2009-12-22
> **DillByrne said:**
> did he install any add ons or mess with connection settings?


He says he didn't. He was just browsing when all of a sudden he couldn't open a new tab or window or get it to search anything off of his present window.

---

### Post by kyate on 2009-12-22
> **houseworkshy said:**
> Alternatively use synaptic package manager to completely remove firefox and then reinstall it.

I tried this. It all worked successfully but then I got a message saying that "Firefox has been updated, on order for these to take affect, Firefox must be restarted, please close existing firefox window." There was no firefox window open. And when I clicked to open the browser, the same things occur as stated in my first post.

So I restarted my laptop and clicked to open Firefox. It worked.

Thank you thank you all. Stupid boyfriend -.-

---

### Post by collinp on 2009-12-22
Run firefox from terminal, like so:
```
firefox
```

And post the output here. (In CODE tags, please!)

---

### Post by lovinglinux on 2009-12-22
For future reference, see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

