---
title: "Can't add a Bookmark or Internet shortcut to Cairo Dock?"
date: 2010-05-23
forum: General Help
---

### Post by schwabdale on 2010-05-23
I would like to add a Icon on the Cairo dock that launchs a specific website. I would like to do this without Prism. 

Anybody know how to do this?

---

### Post by Oblivion_4 on 2010-05-23
sure you can, but I'm not sure that it will be worth it. All you have to do is

1. right click cairo-dock
2. click add which will open up a submenu
3. click add a custom launcher
4. this will open up a new window with four important fields: Launcher Name, Command to run on click, image name or path, and name of the container
5. The only field that matters in this discussion is command to run on click. In this field type in /usr/bin/firefox thesiteyouwanttogoto.com

For example /usr/bin/firefox ubuntuforums.org will open up a new instance of firefox or a new tab at the page ubuntuforums.org

However I doubt this will be effective at all. It would probably just be alot simpler to use bookmarks in my opinion

---

### Post by schwabdale on 2010-05-23
Thanks! That worked great! 

One more quick question... How do you add multiple "Show Desktop" 
Icons to the dock. I want to add them to the same dock.

---

### Post by schwabdale on 2010-05-24
That command worked. The only issue I have now is.. I can only open one instance of Firefox. If I click on this shortcut from Cairo dock and have another instance of firefox open, it just changes the page I was at. 

How do I open it in a different window?

---

### Post by fabounet on 2010-05-25
you should use the extra option "don't mix with the taskbar icon"
so that they don't link with the firefox window.
because all your launchers are "firefox" launchers and therefore they point on the same firefox window.

---

### Post by schwabdale on 2010-05-25
Thanks! That worked!

---

