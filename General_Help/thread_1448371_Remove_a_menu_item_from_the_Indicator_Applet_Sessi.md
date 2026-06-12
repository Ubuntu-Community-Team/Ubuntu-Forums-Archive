---
title: "Remove a menu item from the Indicator Applet Session"
date: 2010-04-06
forum: General Help
---

### Post by anonymousturtle3 on 2010-04-06
The indicator applet session gnome-panel applet (the one that lets you change your status for empathy/pidgin, logout, switch user, etc.) has the suspend and hibernate options. My computer will not suspend or hibernate properly (every time I try to wake it up, the hard drive will work for about 4 minutes and the screen will stay blank so I have to restart) and I would like to remove those items from the menu. 

I would just like to know if there is a way to remove the hibernate and suspend items in the indicator applet session menu. I've already tried browsing around gconf-editor to no avail. If it is not possible, let me know.

Thanks for your help.

---

### Post by dyslexia on 2010-07-19
Bump.   I only need the 'Hibernate' item removed, or a way to rename it 'Crashnow'?

---

### Post by EmanresuusernamE on 2010-07-20
Open up gconf-editor.
/apps/inidcator-session
Check the values that you don't want to see.

---

### Post by shinepuppy on 2010-11-28
Hi All,
I have a slightly similar/different issue. My Lenovo Ideapad Y560 suspends properly when I select it from the indicator applet, but it exhibits the same symptoms as anonymousturtle3 if I simply close the lid.

Can someone help me figure out how I can make the lid close event call the same routine as the 'suspend' event via the indicator applet?

thanks :)

---

