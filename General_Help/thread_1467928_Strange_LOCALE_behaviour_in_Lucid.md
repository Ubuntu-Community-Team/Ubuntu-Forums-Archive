---
title: "Strange LOCALE behaviour in Lucid"
date: 2010-05-01
forum: General Help
---

### Post by WakkiTabakki on 2010-05-01
Hi all
After the upgrade to Lucid I have this strange behaviour related to locales. 

I want all my dates, time, currency and so on in Swedish format, but out of old habit I want my language set to british English. In Lucid, the language tool (System->Administration->Language Tool) gives you two sections, one "Language" and one "Text". According to what I understand the Language-section should change the language in the applications, while the Text-section changes formatting of dates, currencies etc.. in short, this is precisely what I want; Language is now set to English, and Text is set to Swedish.

I now have some issues (just examples, there are more strange things here and there):
- The language of applications are mixed! Examples attached: In Firefox some menu items are in swedish while most are in English; CompizConfig settings is a complete mess, Swedish (most quite bad translations) and English is all over the place

- The Zotero Firefox plug-in is completely in Swedish, while dates are in English format (except that time is in 24hrs-format)

- In Thunderbird, all is fine except it seems any plugins I install will be in Swedish (e.g OpenPgp)

Is there a better approach in making the language settings, is this a bug or am I missing something?

All the best!
/N

---

### Post by spangaer on 2010-05-03
I'm not entirely sure, but I think I had the same problem.

- Migration from 9.10 to 10.04.
- Default language set to dutch nl-be. (family computer)
- My desktop set to us english
- resulting in mixed dutch english gnome ui

When I looked arround a bit.
"locales" command told me that env var LANG was set to us english, but LANGUAGE var was set to nl be. So apparently selecting language (e.g. at login) sets the one but not the other

I was finally able to fix it by adding
export LANGUAGE="en_US.utf8"
to .profile in my home dir.

Took quite a while to find this.

---

### Post by WakkiTabakki on 2010-05-05
Hoi spangaer
En bedankt voor de input!

It turns out (I think) that the LANGUAGE variable is set by the "Language" section in the language section tool, and LANG by the "Text" section.
After fiddling about with this a bit, I think that the underlying problem is that applications doesn't treat these two variables in the way they are intended to... E.g. when installing add-ons in Thunderbird, it seems that it looks at the LANG variable when choosing extension language, while Thunderbird itself looks at the LANGUAGE variable. Thus, my Thunderbird was in English, while all extensions were in Swedish.

The workaround I use now is to set LANGUAGE = en_GB.UTF-8 and LANG = en_DK.UTF-8 (English language with Danish locale, which is close enough to Swedish).

/N

---

### Post by clubsoda on 2010-05-06
Another strange thing I noticed in the **Language for menus and windows** tab is that if one wishes to use a "minor" version of english, it must be accompanied by the U.S. version. For example,```
English (United Kingdom)
Japanese
English (United States)
```displays menus in Japanese.
I had to set```
English (United Kingdom)
English (United States)
Japanese
```to get english menus.

---

### Post by dcstar on 2010-05-07
Also check that your /etc/default/locale file is correct.

---

