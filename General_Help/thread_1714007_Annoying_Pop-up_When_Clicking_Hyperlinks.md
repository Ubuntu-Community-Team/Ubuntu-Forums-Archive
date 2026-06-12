---
title: "Annoying Pop-up When Clicking Hyperlinks"
date: 2011-03-24
forum: General Help
---

### Post by mrkeef on 2011-03-24
About a month ago I started getting an annoying popup when clicking on hyperlinks that asks me to choose Open with firefox, send URL, open with Mozilla or Open with Opera.

Since I've picked Opera as my default for web browser it should be obvious that's what I want. What is really annoying is that it does this when I double click on the address in the browser's address bar, then I go to edit the address and find that it isn't happening as expected.

Can someone please tell me how to turn this "feature" off?

Thanks

Keith

---

### Post by Krytarik on 2011-03-24
Please do this:
- press Alt+F2
- enter "gconf-editor"
- browse to "/desktop/gnome/url-handlers/http"
- check the value of "command", you may simply put the command for Opera from "Preferred Applications" in there
- check if it's "enabled"
- do the same for "/desktop/gnome/url-handlers/https"

Greetings.

---

### Post by mrkeef on 2011-03-24
Thanks but I've already got those options selected.

---

### Post by Krytarik on 2011-03-24
You should have an option in Opera to set it as the default web browser. Did you already try that?

---

### Post by mrkeef on 2011-03-24
Opera is definitely the default browser.

I've just clarified the actual behaviour of what's happening.

If it's an actual link opera oopens as expected. But if the URL is just text as happens in the browser address bar or in some emails where you just have the URL that's when the popup appears.

---

### Post by Krytarik on 2011-03-24
How about this command?:
```
sudo update-alternatives –config x-www-browser
```

---

### Post by mrkeef on 2011-05-17
After trying several options including upgrading to 11.04, I discovered this is only a problem when I am running Cairo-Dock.

Does anyone know how to fix this?

Thanks

Keith

---

