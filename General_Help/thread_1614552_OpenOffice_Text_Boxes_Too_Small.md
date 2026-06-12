---
title: "OpenOffice Text Boxes Too Small"
date: 2010-11-05
forum: General Help
---

### Post by mocha on 2010-11-05
Just upgraded a box to Maverick and noticed that all of the text boxes inside of OpenOffice applications are "squished" slightly to the point where you can't make out everything that you type into them.

For example, the "find" dialog box.  A letter such as "j" gets cut off at the bottom and looks like an "i".

Is this a theme or font problem?  I tried different themes and reloading font settings.  What engine does Open Office use to render its GUI?  Maybe that would point me in the right direction to look for configuration regressions.

I attached a screenshot.

---

### Post by Hagar Delest on 2010-11-06
Works fine for me but I use the vanilla version (see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)). Here is the same dialog under 3.3RC2.

---

### Post by mocha on 2010-11-07
Thanks for the response.  I started thinking and realized that it might have something to do with my gtk theme.  I was right.  I changed the theme I was using for gtk controls and now the combo box heights are correct.

---

