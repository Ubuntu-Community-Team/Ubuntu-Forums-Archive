---
title: "icons all disappear, unable to launch applications, odd stuff"
date: 2011-01-27
forum: General Help
---

### Post by AKADriver on 2011-01-27
System: Dell Inspiron 6000 laptop
Ubuntu version: completely stock Maverick install

After using my laptop for about half an hour to an hour, the following odd symptoms appear, usually while using Firefox:
[LIST]
[*]Firefox is unable to display web pages, displaying a Javascript error.
[*]The notification icons all disappear.
[*]The icons in the application launcher disappear, but the menus are still accessible - however selecting an application has no effect.
[*]The shutdown menu is inaccessible, so the only way to recover is to hard reset. 
[/LIST]

It doesn't seem to be a heat issue, the laptop isn't getting warm.

---

### Post by Krytarik on 2011-01-27
Take a look into "~/.xsession-errors" for error messages after this happened next time.

---

### Post by AKADriver on 2011-03-16
For what it's worth, I've pinpointed the problem to Firefox itself. I found the Firefox problems (but not the other GNOME issues) happening on the CentOS 5 box I use at work. Using Chrome instead of Firefox I haven't had any problems on my Ubuntu laptop.

Both systems are using some variation of Firefox 3.6.

---

### Post by Krytarik on 2011-03-16
Maybe a Firefox add-on is the culprit? Do you use the same at both systems?

About the other issues: It may be that the window manager is causing them. Do you have desktop effects enabled, thus Compiz running? If so, try replacing it with Metacity to narrow down the issue:
- press Alt+F2
- enter
```
metacity --replace
```

---

