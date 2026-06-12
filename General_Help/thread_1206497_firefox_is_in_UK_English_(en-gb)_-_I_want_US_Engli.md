---
title: "firefox is in UK English (en-gb) - I want US English (en-us)"
date: 2009-07-07
forum: General Help
---

### Post by arch0njw on 2009-07-07
I went into the options and tried to select my language.  It *says* that the selected language is "en-us".  I then tried just "en".  No luck.  When I try to spell things like color, they are marked as being misspelled.

I have nothing against out cousins across the pond; I'd just like to spell things the incorrect US way for my other incorrect US brothers and sisters.  ;^)

Anyone else have this problem with FF and know of a/the fix?  I have the same version on a Windows machine and I don't have the same problem.  So it makes me suspect the Ubuntu package.

Linux xxxxxx 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

---

### Post by yeats on 2009-07-07
In Firefox, type "about:config" (w/o quotes) into the address bar, then search for these two Preference Names:

general.useragent.locale
spellchecker.dictionary

you can double click on them and change them to "en-US" (again, w/o quotes).

---

### Post by arch0njw on 2009-07-07
> **chrissharp123 said:**
> In Firefox, type "about:config" (w/o quotes) into the address bar, then search for these two Preference Names:

general.useragent.locale
spellchecker.dictionary

you can double click on them and change them to "en-US" (again, w/o quotes).

That was interesting.  My locale was "en_US".  My dictionary was en_AU.

Thanks!!!

---

### Post by danwood76 on 2009-07-07
> **arch0njw said:**
> When I try to spell things like color, they are marked as being misspelled.


Thats because it's spelt 'colour' :D

I thought firefox uses the system defaults when you install?
So it should set everything to the Ubuntu default language.

---

### Post by scouser73 on 2009-07-07
> **chrissharp123 said:**
> In Firefox, type "about:config" (w/o quotes) into the address bar, then search for these two Preference Names:

general.useragent.locale
spellchecker.dictionary

you can double click on them and change them to "en-US" (again, w/o quotes).

Thanks for this tip, my spellchecker was set to en-US, I've now set it to en-GB.

Once again, thanks.

---

### Post by yeats on 2009-07-07
Happy to help.  There is also a FF add-on (of course :-) ) that lets you change this from a menu and avoid all the about:config business:

[https://addons.mozilla.org/en-US/firefox/addon/1333](https://addons.mozilla.org/en-US/firefox/addon/1333)

Could be useful in a multi-lingual environment.

---

### Post by 1clue on 2009-11-02
I hate to resurrect a months-old thread, but I found this thread extremely helpful.  I knew about one of the firefox settings, but not the dictionary one.

I find it baffling that Firefox has a default which is not the system default.

I find it baffling that, given the above circumstance, Firefox requires a plug-in to set the above settings in a normal GUI control panel.

I find it frustrating that Firefox keeps switching away from the user-set default and goes back to the incorrect Firefox-only default.

I find it extremely helpful that, given all the above, somebody can put an answer in such a concise and direct fashion.  I wish the information in this thread were a sticky, or a WIKI entry.

Thank you.

---

### Post by GiveLove on 2009-11-27
Thank you for this very helpful thread!!! 

I've been having this problem for quite some time now of my Firefox dictionary using the British English dictionary. I tried install a US English dictionary add-on. But it did not fix the problem. As looking at the "spellchecker.dictionary" setting in about:config, it was still set to en-GB. So I just modified it to en-US, and uninstalled the dictionary add-on. And all is good now. Words come out spelled correctly: color, flavor, offense, and so on. LOL  Thanks again.

Peace & Love

---

### Post by Fenris_rising on 2009-11-27
Yep I'd like to add my thanks. I have been 'criticised' for my spelling since installing Ubuntu all those months ago. Now I can spell words like Colour without it being underlined =D

regards

Fenris

---

