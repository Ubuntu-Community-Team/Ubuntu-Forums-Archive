---
title: "Chromium doesn't remember I set it default browser"
date: 2011-06-29
forum: General Help
---

### Post by KennyGJE on 2011-06-29
It keeps asking if I want to set it as default.
I always press 'yes' and when I exit and open it again it asks the same question...
If I say 'never ask me again' it stops, but continues after I reboot the computer... Help?

EDIT: I also deleted Firefox

---

### Post by wolfen69 on 2011-06-29
If you don't mind deleting your chromium settings, you could delete your config file and see if it works. You could rename your current chromium config file to something else just to have it around to put it back. The file is located in .config.

---

### Post by KennyGJE on 2011-06-29
> **wolfen69 said:**
> If you don't mind deleting your chromium settings, you could delete your config file and see if it works. You could rename your current chromium config file to something else just to have it around to put it back. The file is located in .config.

Thanks! Works like a charm :D:D

---

### Post by ssreddy555 on 2011-06-29
Better way to set the default browser:

System > Preferences > Preferred Applications > Web Browser > Chromium.

By default, it is set to FF.

---

### Post by ssreddy555 on 2011-06-29
Better way to set the default browser:

System > Preferred Applications > Web Browser > Chromium.

By default, it is set to FF.

---

### Post by Manoel on 2011-08-22
> **ssreddy555 said:**
> Better way to set the default browser:

System > Preferred Applications > Web Browser > Chromium.

By default, it is set to FF.

It SHOULD be the best way to set it, but it works strange to me after upgrading from Ubuntu 10.10 to 11.04. I had Seamonkey as my default browser and now it should also be, but when I go to Preferred Applications, there it is only Firefox showing up. The same with mail app: I had Seamonkey but now it only shows Evolution.

Incredible as it may seem, when I go to terminal and type:

```
sudo update-alternatives --config x-www-browser
```

it tells me that Seamonkey is already the default web browser!

Anyway, when I try to open a URL from some app, it goes to Firefox, so the preference marked by "Preferred Apps" must be taking preference over the other. :confused:

---

### Post by Manoel on 2011-08-22
This bug is making things harder in these cases that the default preferred browser is not correctly detected: [http://ubuntuforums.org/showthread.php?t=1776094](http://ubuntuforums.org/showthread.php?t=1776094)

---

### Post by Manoel on 2011-08-22
I've tried [this approach]("http://askubuntu.com/questions/16621/how-to-set-the-default-browser-from-the-command-line") but add that line:

```
export BROWSER=/usr/bin/seamonkey
```

 doesn't make a difference! :-(

---

### Post by Manoel on 2011-08-22
Executing **gconf-editor** worked!

I had to change these items' command

```
/desktop/gnome/url-handlers/http 
/desktop/gnome/url-handlers/https 
/desktop/gnome/applications/browser/exec
```

from *firefox* to *seamonkey*
and now seamonkey REALLY works as my default browser.

---

### Post by Manoel on 2011-08-22
But look out!

Every time I open Firefox it makes that old Internet Explorer dirty trick and puts itself as default browser again! :(

---

