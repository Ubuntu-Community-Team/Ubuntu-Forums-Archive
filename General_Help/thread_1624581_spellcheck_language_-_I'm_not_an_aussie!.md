---
title: "spellcheck language - I'm not an aussie!"
date: 2010-11-17
forum: General Help
---

### Post by PintOfBitter on 2010-11-17
I can't figure out why my spellcheck is thinking I need to spell words like "colour" etc.  Apparently the language settings are on the wrong English variant, but I can't find the setting - my language setting seem to be correct.

I can't find ANYTHING on this - anyone?  Please?

---

### Post by dcstar on 2010-11-17
> **PintOfBitter said:**
> I can't figure out why my spellcheck is thinking I need to spell words like "colour" etc.  Apparently the language settings are on the wrong English variant, but I can't find the setting - my language setting seem to be correct.

I can't find ANYTHING on this - anyone?  Please?

It depends entirely on what dictionaries you have installed and that is set by the Locale you select on install.

BTW, different apps use different dictionary systems, so unless you actually specify exactly what you are using you will get no specific advice on what to check.

---

### Post by arvevans on 2010-11-17
Go to "System-->Administration-->Language Support".
This will let you set your default language, or languages.
There are some other dictionaries but most will be automatically selected when you set your preferences via the above administrative tool.  If a specific application does not use your preferred dictionary, then check it's configuration and preference settings to insure that it is set correctly.

---

### Post by PintOfBitter on 2010-11-18
I'm noticing it in firefox...  thought it was global, but I just checked in openoffice, and it seems OK.  I'll need to poke around in firefox I guess.

Thanks

---

### Post by Joeb454 on 2010-11-18
> **PintOfBitter said:**
> I'm noticing it in firefox...  thought it was global, but I just checked in openoffice, and it seems OK.  I'll need to poke around in firefox I guess.

Thanks

Click Edit > Preferences, then go to the 'Content' tab.

This is where you can change your language, if needs be :)

---

### Post by bouncingwilf on 2010-11-18
Its obviously because of your name! Only a Brit truly understands a pint of bitter. Oh! to slowly sup a pint of Young's special ( served at 52 Deg. F of course).


Bouncingwilf

---

### Post by PintOfBitter on 2010-11-20
ohhhh you've got me drooling.  The best I get here is Boddy's in a can with the widget.

I looked into the settings.  There's nothing out of the ordinary there - english (US) seems to be default.

---

### Post by WorMzy on 2010-11-20
> **bouncingwilf said:**
> Its obviously because of your name! Only a Brit truly understands a pint of bitter. Oh! to slowly sup a pint of Young's special ( served at 52 Deg. F of course).


Bouncingwilf

Fahrenheit? What foreign devilry is this? Begone!

OP: You can install different language dictionaries from here: [https://addons.mozilla.org/en-US/firefox/language-tools/](https://addons.mozilla.org/en-US/firefox/language-tools/)

Uninstall any others that you don't want from Tools -> Addons (Ctrl+Shift+A)

---

### Post by mulad on 2011-02-06
I was seeing this on one of my boxes, but I managed to fix it.

[LIST=1]
[*]Type "about:config" in the address bar
[*]If you get a warning message about how this might break your browser, acknowledge it and continue
[*]In the search field at the top of the about:config page, type "spell"
[*]Look for the "spellchecker.dictionary" line.  This is probably currently set to "en_AU"
[*]Right-click on the line and select "Reset"
[/LIST]

I think that causes the browser to fall back to using the locale variables (you can see what they are set to by typing "locale" in a terminal window).

---

### Post by Maxfield Solar on 2013-02-17
I had this problem as well. Just go to a text box then right-click, then select "Languages", then select "English (United States)"

---

### Post by howefield on 2013-02-17
Old thread closed.

---

