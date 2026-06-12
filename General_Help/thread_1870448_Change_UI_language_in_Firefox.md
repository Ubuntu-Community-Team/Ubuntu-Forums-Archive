---
title: "Change UI language in Firefox"
date: 2011-10-27
forum: General Help
---

### Post by mahy on 2011-10-27
As a part of my Spanish-learning initiative, I'd like to switch the browser (Firefox 7.0.1 in my case) into Spanish. Just that, not the entire desktop environment (Xfce)! The rest should stay in English for now. And I also want to use the *packaged* Firefox.

So I browsed some forums (including this one), downloaded the spanish lang pack (firefox-locale-es) and also changed the property 'general.useragent.locale' in Firefox's 'about:config' into 'es-ES' (was orignally 'en-US'). Unfortunately that didn't help. So I browsed and browsed, but couldn't find any other solution. :( There seems to be no option in Firefox to force the UI language.

What exactly am I doing wrong? Is it possible to have desktop env in one language and (packaged) Firefox in another? I'm under impression that Linux desktop environments' philosophy is to prevent such situation at all costs...

Any help will be much appreciated. Thx.

---

### Post by lovinglinux on 2011-10-27
[https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/](https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/)

---

### Post by mahy on 2011-10-31
> **lovinglinux said:**
> [https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/](https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/)

I appreciate your effort, but your suggested solution *does not* work. It does not change the Firefox UI language. You can easily try it yourself to prove it. In other words, I doubt it works for you.

Pleas guys, this can't be that difficult! :confused:

---

### Post by infinitybot on 2011-10-31
There are international versions of firefox available

[http://www.mozilla.org/en-US/firefox/all.html](http://www.mozilla.org/en-US/firefox/all.html)

Hope This helped you :)

---

### Post by lovinglinux on 2011-10-31
> **mahy said:**
> I appreciate your effort, but your suggested solution *does not* work. It does not change the Firefox UI language. You can easily try it yourself to prove it. In other words, I doubt it works for you.

Pleas guys, this can't be that difficult! :confused:

I used this add-on a couple of months ago, but now that you mentioned, I tested again, just to make sure. See my screenshots.

First make sure you have the firefox-locale-es installed and activated. You can check that from the add-ons manager (about:addons). Then install the extension, open the extension preferences and tick the option "General >> Switch the following locale related settings >> User Interface Language". Then select the Spanish locale in the "Locales" tab and close the preferences. Click the Quick Locale Switcher button in the add-ons bar at the bottom and select Spanish. It will ask if you want to restart Firefox. Click OK.

---

### Post by mahy on 2011-10-31
> **lovinglinux said:**
> I used this add-on a couple of months ago, but now that you mentioned, I tested again, just to make sure. See my screenshots.

First make sure you have the firefox-locale-es installed and activated. You can check that from the add-ons manager (about:addons). Then install the extension, open the extension preferences and tick the option "General >> Switch the following locale related settings >> User Interface Language". Then select the Spanish locale in the "Locales" tab and close the preferences. Click the Quick Locale Switcher button in the add-ons bar at the bottom and select Spanish. It will ask if you want to restart Firefox. Click OK.

Thanks a lot, I already found a solution. My "Locale Switcher 3" addon has NO configurable preferences (dunno why, maybe I installed a wrong addon), so I can't follow your approach. However, after some trial and error, I found the key in about:config which does the trick:

intl.locale.matchOS -> set to false

and now the language I set in Locale Switcher takes effect!

---

