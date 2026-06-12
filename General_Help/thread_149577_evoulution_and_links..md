---
title: "evoulution and links."
date: 2006-03-24
forum: General Help
---

### Post by syklitengutt on 2006-03-24
Hi. I have this problem with evolution.
When I click links I get in mail, it opens a new browser, and just loades the 
homepage, not the selected page in my mail.
Any ideas? It works great in Thunderbird, but not in amsn eather.

---

### Post by syklitengutt on 2006-03-24
any ideas?

---

### Post by dcstar on 2006-03-24
[QUOTE=syklitengutt]Hi. I have this problem with evolution.
When I click links I get in mail, it opens a new browser, and just loades the 
homepage, not the selected page in my mail.
Any ideas? It works great in Thunderbird, but not in amsn eather.[/QUOTE]
System-Preferences-Preferred Applications-Web Browser

Mine is a custom one with the contents:
```
/usr/local/swiftfox/firefox "%s"
```
The "%s" is important, as it directs the browser to use the info passed from the app to open the web site.
-------
And I found more:
Applications-System Tools-Configuration Editor-Desktop-Gnome-url handlers-http

The "command" should have something like the code above (for your default browser).

Also check the https entry is the same.

---

