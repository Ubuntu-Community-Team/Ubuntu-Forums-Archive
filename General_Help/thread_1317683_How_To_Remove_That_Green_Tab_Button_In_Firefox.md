---
title: "How To Remove That Green Tab Button In Firefox"
date: 2009-11-06
forum: General Help
---

### Post by Ghostpup on 2009-11-06
I much prefer to install the "Toolbar Buttons" Add-on and drag a "New Tab" button right in line with my forward and back buttons.

Go to your home folder and click on [COLOR=Blue]View > Show Hidden Files[/COLOR]. Then Go To [COLOR=Blue].mozilla/firefox/xxxxxxxx.default/chrome[/COLOR]. (Of course, the beginning of the name of that folder isn't really xxxxxxxx.) If a file doesn't exist which is named, exactly: userChrome.css then right-click in a blank area and go to [COLOR=Blue]Create Document > Empty File[/COLOR] then rename that file (you guessed it) [COLOR=Blue]userChrome.css[/COLOR]. Then paste the following line of text in (including the dot at the beginning) [COLOR=Blue].tabs-newtab-button {display: none;}[/COLOR] Save and close the file and that should do it.

---

### Post by winotree on 2009-11-06
Nice first post.  Welcome to the forum.  :D

---

