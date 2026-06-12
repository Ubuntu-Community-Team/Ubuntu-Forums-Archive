---
title: "Docky + Chrome Web Apps = Broken Docky"
date: 2010-10-26
forum: General Help
---

### Post by Matthileo on 2010-10-26
I tried adding a chrome web-app shortcut for gmail. I got tired of it and deleted it from the menu.

The problem is that now when chrome is open it shows a gmail icon in Docky instead of its own icon.

I completely removed docky and all of its data, then reinstalled, and the problem stayed.

What can I do??

~matt

p.s. see attachment

---

### Post by Matthileo on 2010-10-26
Nevermind. I fixed it.
Apparently chrome hides the web-app .desktop files all over the place, and they all have to be deleted.

./home/matt/.local/share/applications/chrome-https___mail.google.com_mail.desktop

./home/matt/.gnome/apps/chrome-https___mail.google.com_mail.desktop

---

### Post by JEJ514 on 2010-11-02
Matt--thanks!  This exact thing happened to me and your posted solution solved it for me!  Thanks for going to extra step and letting us know what worked for you.

---

### Post by AnArchAndroid on 2011-02-08
Thanks, I have the same issue. Thanks for posting your solution.

I'll try deleting the .desktop files when I get home tonight without uninstalling docky or chromium, I'll update with the results.

---

