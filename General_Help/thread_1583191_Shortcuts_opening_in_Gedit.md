---
title: "Shortcuts opening in Gedit"
date: 2010-09-27
forum: General Help
---

### Post by dyslexicfurby on 2010-09-27
I have an internet shortcut on my desktop. It opens in Gedit instead of opening Firefox. How do I fix this?

---

### Post by TeoBigusGeekus on 2010-09-27
Right click it -> Open with.

---

### Post by WorMzy on 2010-09-27
Right-click -> Properties -> Open With

For a more permanent solution.

---

### Post by dyslexicfurby on 2010-09-27
If only it was that easy. I right click on the shortcut and I have:
Open
Cut
Copy
Paste into folder
Make link
Rename
Copy to
Move to
Move to trash
Stretch icon
Restore icon size
Compress
Send to
Properties

And there is no "open with" in properties. Just 4 tabs: Basic, Emblems, Permissions, Notes. Nothing that looks like 'open with'.

The thing is it USED to work and I didn't change anything so I don't know why it's not working.

---

### Post by dyslexicfurby on 2010-09-29
Am I allowed to bump?

---

### Post by mc4man on 2010-09-29
create an empty file named 1.html, then r.click -> properties -> open with

Choose firefox and your shortcut (or any html file) will now default back to firefox

edit:
if you wished to ck. out (and another way to fix), go
```
gedit ~/.local/share/applications/mimeapps.list
```

look for this line
text/html=
The first listed .desktop is the default, you would have had this
text/html=gedit.desktop;firefox.desktop;
or just
text/html=gedit.desktop; 

What you should have now after above is (or edit as such as alt. fix

text/html=firefox.desktop;gedit.desktop;

---

### Post by dyslexicfurby on 2010-09-30
Thank you! That's exactly what I was looking for. It works properly now. What I don't get is why the default 'open with' changed in the first place. I guess I'll never know.

---

