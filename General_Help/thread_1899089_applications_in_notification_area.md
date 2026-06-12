---
title: "applications in notification area"
date: 2011-12-22
forum: General Help
---

### Post by netopalis45 on 2011-12-22
I have some applications that only show up in the notification area but with Oneric I have not been able to use them because of the lack of a notification area. Is there something I can do to get it back? Otherwise I will not be able to use some things that I may need to.

---

### Post by pretty_whistle on 2011-12-22
Right click the panel and select "add to panel".  Then when the list comes up select "Indicator-applet-complete".

---

### Post by netopalis45 on 2011-12-22
I have tried to right-click on the panel and nothing happens

---

### Post by polki@mac.com on 2011-12-23
Alt+right click, or if you're using Compiz alt+super+right click sometimes work better.

---

### Post by netopalis45 on 2011-12-23
Alt right-click and Alt-Super right-click don't do anything either. Can you even change the panel in Unity?

---

### Post by sikander3786 on 2011-12-23
Notification area is still there but it only displays the applications that are whitelisted. You need dconf-tools. Install it from Terminal:

```
sudo apt-get install dconf-editor
```

Now press Alt + F2 and type 'dconf-editor' and start it. Get to Desktop > Unity > Panel and edit 'systray-whitelist' value. Delete everything and type ['all'] in its place. You'd probably need to relogin.

Take a look at 'Install dconf-editor and tweak some more settings' section here for more details:

[http://www.tuxgarage.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://www.tuxgarage.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

---

### Post by netopalis45 on 2011-12-23
I have done that and still am not able to add anything to the panel. Nothing happens if I right-click on the panel unless its over something that is already there and all I get is the menu for that application.

---

