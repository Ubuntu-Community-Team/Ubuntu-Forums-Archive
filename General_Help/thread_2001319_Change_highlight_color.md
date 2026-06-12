---
title: "Change highlight color?"
date: 2012-06-10
forum: General Help
---

### Post by TheGuyWithTheFace on 2012-06-10
I used to have my Ubuntu set up so the highlighter was a different color from the regular orange. Then, because of a silly mistake when I was playing around with different desktop environments, I decided to reinstall 12.04. I had 4 copies of all my data, so no worries there, but I can't find the article I read about how to change the highlighter color. 

I know I used dconf Editor to modify  org->gnome->desktop->interface gtk-color scheme, but instead of simply entering a color, I need to specify the name of whatever it is I'm changing. 

Any ideas what the name of the highlighter thingy is?

---

### Post by mc4man on 2012-06-10
One simple way is shown here, either thru dconf-editor or a gsettings command
The 'highlight' color is 
 selected_bg_color
[http://ubuntuforums.org/showthread.php?t=1999363](http://ubuntuforums.org/showthread.php?t=1999363)

---

### Post by TheGuyWithTheFace on 2012-06-10
Thanks!

---

