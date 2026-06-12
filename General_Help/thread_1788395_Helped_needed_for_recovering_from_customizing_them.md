---
title: "Helped needed for recovering from customizing themes"
date: 2011-06-22
forum: General Help
---

### Post by fallofshadows on 2011-06-22
Hey guys,

I was playing with Emerald today, trying to make my desktop look nicer. Well, the themes didn't end up working out the way I wanted, so I figured I'd just go back to my other theme. That's when I started running into problems.

Everything else has gone back to normal. I've regained compiz functionality, so all of my effects are back. Unfortunately, when I click on a theme from the Appearance box (right click on desktop > change desktop background > themes) everything except my window's top bar (the one with the buttons and title) changes. I uninstalled emerald, hoping this would fix it, but it just changed my top menu to this weird orange bar.

If I run "metacity --replace" everything goes back to looking normal, but I lose all of my compiz ability. Running "compiz --replace" puts the animations and whatnot back, but I'm stuck with that orange bar again.

Does anyone know how to fix this?

---

### Post by cottfcfan on 2011-06-22
Try installing fusion-icon & make sure that the window decorator is set to GTK.

---

### Post by fallofshadows on 2011-06-23
How do I set the decorator to GTK?

Edit: Finally, by following a guide I found on the internet (thanks to your mentioning GTK themes) I was able to reset my appearance. Turns out I had to open the gconf-editor and go through a couple of folders before checking a box that reads "use metacity_themes".

Thanks for the hint, I'm glad to have this all sorted out :) Now one final question: Is there a way to learn how to change around themes and such without all of this happening again? This whole deal of switching up what engine my windows use is sortof confusing to me.

---

