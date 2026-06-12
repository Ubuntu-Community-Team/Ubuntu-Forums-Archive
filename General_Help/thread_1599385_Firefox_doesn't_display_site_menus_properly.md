---
title: "Firefox doesn't display site menus properly"
date: 2010-10-17
forum: General Help
---

### Post by danbaark on 2010-10-17
I'm using Firefox 3.6.10 for Ubuntu 10.10 with the smooth-scaling ppa (only addons I'm using are Firebug and the Ubuntu modifications pack). 

Several sites with navigation menus the menu is spread over two lines when it obviously shouldn't be (eg. The Telegraph online, BBC News...) this happens no matter what the zoom level is set to. Chromium renders all these pages normally.

Any one know what's going on? Screenshots attached. Thanks very much

---

### Post by Vaphell on 2010-10-17
it's very simple, firefox uses a font that doesn't fit in 1 line. I'd blame webdesigner more than firefox because the page should be shown well without any assumptions made (specific OS, specific fonts available, pixel perfect layouts). Chrome happens to pick different defaults but FF is not guilty really. As you can see ff uses some Serif font by default, Chrome some sans-serif.

do you have msttcorefonts (package with windows fonts) installed? This may help because that page probably needs arial or something like that.

if that doesn't help you can play with firefox preferences to set specific font as the default in case FF can't find a font specified in webpage code.

---

### Post by danbaark on 2010-10-17
Thanks for that, I suppose it's debatable whose fault it is but I do think it would make sense for Firefox's default font to render sites as mainstream as the BBC correctly (as it does on windows and as Chromium does on Ubuntu)

Anyway thanks for the help, got them looking right by using the font liberation-serif size 18 as default.

---

### Post by Vaphell on 2010-10-17
but it's the webdesigner role to specify the path of graceful degradation, for example
'try Arial -> SomeOtherFont -> YetAnotherFont -> some-generic-font-family'
BBC did only something like 'try Arial, period'. If the system doesn't have that font and has no idea what substitutes of that font are nor what family it belongs to, then anything can happen.
for firefox Arial is just a character string, it takes it and asks the system - 'give me font named Arial, if not then give me something else, for example my default'.

Writing cross platform software is time-sensitive enough and mozilla is not as rich as google to test compatibility with thousands of 'high-profile' sites. Yes you can include some hacks in your standard-compatible browser but it breaks the internet in the long run. Internet explorer 6 and it's questionable legacy is my witness. Websites and browsers should be written to conform with web standards, not the other way around :)

---

