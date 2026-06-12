---
title: "I am beginning to feel sorry to have upgraded to 10.04"
date: 2010-06-04
forum: General Help
---

### Post by DrScum on 2010-06-04
the latest problem being (see my other posts regarding wlan functionality gone) the minimize/maximize buttons on my windows keep dissapearing.

I read the posts regarding replacing emerald and metacity and so on but it doesn't seem to really fix the problem.

The situation is as follows: buttons gone, opening terminal window, entering "emerald --replace" then the buttons are back until I close the terminal window. After that there is only reebooting (reminds me of old Windows times) but the buttons keep being lost.

What can I do?

---

### Post by howefield on 2010-06-04
> What can I do?

Put emerald --replace in your Startup Applications list ?

Or if you use compiz, try loading compizconfig-settings-manager and navigate to the "Window Decorations" plugin and in the Command field, replace compiz-decorator with emerald so it reads

/usr/bin/emerald

---

### Post by quinntar on 2010-06-04
Well I still had problems when I tried to upgrade from a version to another so as for me I make a fresh install each time i want to use the "new" version of ubuntu... I think i had a a similar problem with th buttons but that's when I tried the beta release...
You could save up your data and make a fresh install it always did the trick for me at least.

---

### Post by bwell on 2010-06-04
Just logged into Ubuntu 10.04 and minimize, maximize, close buttons were gone.  howefield's suggestion worked for me since I'm running compiz.

I did the following:

System --> Preferences --> CompizConfig Settings Manager.  Under 'Effects' clicked on 'Window Decoration'.

In the 'Command' field box, I already had emerald --replace so, I replaced it with /usr/bin/emerald --replace.

When I clicked the 'Back' button the buttons appeared.  I have not rebooted the machine to see if the solution stays or not but, they are back for now.

---

