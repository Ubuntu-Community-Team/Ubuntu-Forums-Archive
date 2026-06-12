---
title: "Firefox icons changed"
date: 2012-03-12
forum: General Help
---

### Post by abdulmajid on 2012-03-12
Hey everyone,

I have an issue with the Firefox icons. Let me post the screen shots in order to explain concisely.

[IMG]http://i1125.photobucket.com/albums/l582/abdulmajid88/Screenshotat2012-03-12171400copy.png[/IMG]
This was the Firefox which was shipped with Ubuntu 11.10

[IMG]http://i1125.photobucket.com/albums/l582/abdulmajid88/Screenshotat2012-03-12114739copy.png[/IMG]
And this is the Firefox after the update.

Notice the change in the icons marked with red lines?

I think the icons in the previous version of the Firefox was cleaner and beautiful. How can I change back the icons?

Thank you

---

### Post by abdulmajid on 2012-03-12
Bump...bump...bump

---

### Post by polt on 2012-03-12
Those icons are supposed to be based on your system theme.  I'm not sure why they would change after a Firefox upgrade.  

See this page for more details:

[https://support.mozilla.org/en-US/kb/Navigation%20Toolbar%20items]("https://support.mozilla.org/en-US/kb/Navigation%20Toolbar%20items")

---

### Post by pqwoerituytrueiwoq on 2012-03-12
/usr/share/icons/Humanity/actions/16
take a look in that folder (default theme icons)

[IMG]http://ubuntuforums.org/moz-icon://stock/gtk-refresh?size=menu[/IMG] moz-icon://stock/gtk-refresh?size=menu

---

### Post by kostkon on 2012-03-12
Mozilla changed it in Firefox 9. Now instead of the custom reload and stop icons that Firefox used to have, it now uses the system icons for these two actions.

---

### Post by abdulmajid on 2012-03-12
Is there any way to change it back to previous versions of icons?

---

### Post by pqwoerituytrueiwoq on 2012-03-13
if you have the old icons you can use the userChrome.css file
```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
.search-go-button {
   list-style-image: url("./old-search.png") !important;
}
#urlbar-reload-button {
   list-style-image: url("./old-refresh.png") !important;
}
```you will need to put the images (old-search.png and old-refresh.png) in the same folder as the other file

---

