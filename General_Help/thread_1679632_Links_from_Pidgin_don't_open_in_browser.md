---
title: "Links from Pidgin don't open in browser"
date: 2011-02-01
forum: General Help
---

### Post by sillyfofilly on 2011-02-01
Recently, whenever I click on a link from within a Pidgin chat window, the link will not be displayed in my default browser (Google Chrome), but with a different application depending on the type of link. A web page will be opened in gedit, while an image will be opened in the Eye of Gnome Image Viewer.

I have read that this might have something to do with mimeinfo.cache files, but all of the ones on my system don't list gedit for anything other than text/plain

What is happening when I click on a link in Pidgin, and how can I get it to open my browser?

---

### Post by Krytarik on 2011-02-01
Where does URLs from other apps, i.e. Thunderbird or such, open?

Check the settings in "System -> Preferences -> Preferred Applications".

It seems like the "gnome-open" command gets used instead.

The settings on which apps is by which mimetype are stored in "~/.local/share/applications/mimeapps.list".

---

### Post by sillyfofilly on 2011-02-01
Pidgin is the only program that I've noticed this in, but I might look into it some more later on. For now, I have edited my ~/.local/share/applications/mimeapps.list
Before it included the line

```
text/html=gedit.desktop;
```
which I changed to
```
text/html=google-chrome.desktop;gedit.desktop;
```

and it's working as expected.

---

### Post by Krytarik on 2011-02-01
You could also just remove those entry altogether, the app specified in "System -> Preferences -> Preferred Applications" gets called then.

---

