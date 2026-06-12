---
title: "Odd and frustrating Firefox behavior..."
date: 2009-10-05
forum: General Help
---

### Post by subv3rt on 2009-10-05
Hi guys. I have a problem that's not necessarily Linux/Ubuntu/Whatever related, but this is the only forum I'm a member of that's even close. Hopefully someone can help.

I have a good amount of bookmarks in my bookmarks toolbar. They're all in separate folders that are condensed into one folder to preserve screen real estate. I have also moved the toolbar to be inline with the address bar and all the various buttons.

My problem is that when I initially open up Firefox, it looks like this:

  [IMG]http://ubuntuforums.org/attachment.php?attachmentid=130811&stc=1&d=1254716243[/IMG]


However, this is not how I want it. By default, the bookmarks area is fully collapsed. But if I open up and close the Customize Toolbar thing, it magically fixes it. This is how it should be:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=130812&stc=1&d=1254716243[/IMG]




Hopefully this can be resolved easily. I've dug through my settings, tried disabling various add-ons... I just don't know!

Also, this doesn't happen with the same Firefox profile on my WinXP/7 or OS X machines.


I don't know.






All help is appreciated! Thanks in advance!



.subv3rt

---

### Post by squenson on 2009-10-05
Is it just me or you also don't see any difference between the two images? (I have never been good in the 7 differences game...)

Now I see the difference... but I have no answer...

---

### Post by anonymous_user on 2009-10-05
Can you see it now:

[img]http://www.zwixy.com/images/404823629fixed.png[/img]

---

### Post by Vaphell on 2009-10-05
out of curiosity - what did you do to the menu bar? in case you don't know you can put stuff there too.
i did just that - i moved many things there: back and forward buttons (home is not needed, refresh = f5/ctrl+r, stop=esc), urlbar and search engine

either way use google to find some info about userChrome.css, this file is used to alter default firefox UI

---

### Post by barthel on 2009-10-05
That doesn't look like the default Firefox theme.

Have you tried it with the default theme to see if it's a problem with the theme's code?

---

### Post by subv3rt on 2009-10-05
> **Vaphell said:**
> out of curiosity - what did you do to the menu bar? in case you don't know you can put stuff there too.
i did just that - i moved many things there: back and forward buttons (home is not needed, refresh = f5/ctrl+r, stop=esc), urlbar and search engine

either way use google to find some info about userChrome.css, this file is used to alter default firefox UI
I hide the menu bar via add-on and just hit Alt if i need it.

I've tried digging through config files to edit the .css, but I haven't been able to find anything that resolves my issue.

Thanks for looking though!

---

### Post by subv3rt on 2009-10-05
> **barthel said:**
> That doesn't look like the default Firefox theme.

Have you tried it with the default theme to see if it's a problem with the theme's code?
Yes, I have. I've tried with the default theme, and many other themes and I get the same behavior regardless.

---

### Post by Vaphell on 2009-10-05
i've seen such behavior in the default theme when i tried to do similar thing to that OP did. I packed much stuff in 1 row and when i assumed that URLbar will shrink, surprisingly bookmarks did. It was random, i think that tweaking userChrome.css and applying some strict rules to the UI elements would solve that problem but it might not be easy, you need to know names of these things and such.

---

### Post by lovinglinux on 2009-10-05
> **subv3rt said:**
> Yes, I have. I've tried with the default theme, and many other themes and I get the same behavior regardless.

That happens to me to, regardless of the theme.

What I did was putting the bookmarks in a toolbar that doesn't have auto-sizing elements like the address bar and the search bar. It seems they compete with each other for space and sometimes the bookmarks loose.

Also give it enough space after the bookmarks folder.

---

### Post by anonymous_user on 2009-10-05
See if this helps:

[http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar](http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar)

---

### Post by subv3rt on 2009-10-05
> **anonymous_user said:**
> See if this helps:

[http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar](http://lifehacker.com/5374698/how-can-i-fix-my-disappearing-bookmarks-toolbar)
That did the trick!! w00t!

Thanks so much!

---

