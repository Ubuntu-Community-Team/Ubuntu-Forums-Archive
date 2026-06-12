---
title: "firefox: can't see white text on buttons + owa problems"
date: 2011-09-05
forum: General Help
---

### Post by nik_nah on 2011-09-05
I'm having problems with firefox showing white text on the buttons on most web pages.  It's also having problems with Outlook web access, not showing some images/layout.

I have tried removing .mozilla 
I have tried changing desktop themes(xubuntu)

But same problems, is there anything else I can do to reset firefox?

---

### Post by lovinglinux on 2011-09-05
Open “Edit >> Preferences >> Content” and click the “Advanced” button in the “Fonts & Colors” section, then edit the font size and color. Untick the option “Allow pages to use their own fonts, instead of my selections above”.

---

### Post by nik_nah on 2011-09-05
Thanks for the suggestion, but I'll just end up with the same font for every site.

I logged into another account on the same computer and noticed that it wasn't happening there.
So on the faulty account, I removed .gconf .gconfd .local .gnome2 .gnome2_private

Looks good now, hope it stays that way.

---

