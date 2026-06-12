---
title: "reenable notifications"
date: 2011-11-05
forum: General Help
---

### Post by bryncoles on 2011-11-05
Evening all!

Just this second, I plugged in my internet cable, went to click the search box in Firefox and accidentally clicked 'do not show this notification again' on the message telling me my internet was connected!

But I like those messages.  How do I get it back?  Online documentation is bad (or my Google-fu is weak), and the settings manager -> notifications is strangely option light!

Ideas?

---

### Post by gsmanners on 2011-11-05
Run gconf-editor, navigate to apps/nm-applet, and set the keys whatever way you want.

---

### Post by bryncoles on 2011-11-05
Cheers gsmanners

Ah, did I forget to specify, I'm running xubuntu.  What's XFCE's version of gconf-editor?

---

### Post by gsmanners on 2011-11-05
It's called gconf-editor (both the package and the way you invoke it). :D

---

### Post by bryncoles on 2011-11-05
Victory is ours!  I will send you one internets in the post, sir!

I decided not to do things the easy way though, as trying to run 'gconf-editor' had no effect on my system.  Apparently, I don't have it installed.  

However, following your advice, I located the folder nm-applet and simply deleted the file inside (%gconf.xml).  No I have my lovely notification back, so well done!  Thanks for the help!

---

