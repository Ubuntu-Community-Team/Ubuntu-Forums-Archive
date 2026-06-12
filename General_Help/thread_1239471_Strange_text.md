---
title: "Strange text"
date: 2009-08-13
forum: General Help
---

### Post by Optimus_Jazz on 2009-08-13
Hi,im having a strange problem with regard to text on screen,basically this is the problem
[IMG]http://img218.imageshack.us/img218/2869/screenshotuqq.png[/IMG]
any idears oin how to fix?Thanks

---

### Post by SPr on 2009-08-13
Look in the options or preferences of whichever browser you use and try changing the character encoding until the text is correctly printed.

Which browser is it?

---

### Post by Optimus_Jazz on 2009-08-14
Im using Firefox

The thing is it comes and goes when it pleases,sometimes the webpages will got 80% white for know reason:confused:

---

### Post by soapBAR2 on 2009-08-14
> **Optimus_Jazz said:**
> Im using Firefox

The thing is it comes and goes when it pleases,sometimes the webpages will got 80% white for know reason:confused:

It either sounds like your firefox render engine is borked, or you're missing a bunch of fonts. Firefox->Edit->Preferences->default font-> Change it to something else, see if that works. Also, try seeing if "preferred language" is set to your preferred language. If not, try uninstalling and reinstalling your firefox. If *THAT* doesn't work, try switching browsers, and seeing if the problem also occurs on that browser (preferably try both a firefox based browser like abrowser and a non-firefox based browser like Opera or Konqueror, to try and see if the problem is with firefox or your computer).

If you're still in trouble, try installing a ridiculous amount of fonts:

```
sudo apt-get install xfont*
```

(Warning: on my computer, that amounts to 340MB of fonts) and see if that helps.

---

### Post by Optimus_Jazz on 2009-08-14
cheers ill give that a bash#

---

