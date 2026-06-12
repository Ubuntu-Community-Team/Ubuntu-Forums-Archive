---
title: "ibus chinese -- how to input phrases?"
date: 2009-11-09
forum: General Help
---

### Post by contents on 2009-11-09
Using ibus for the first time since upgrading to Karmic, and I can't figure out how to easily type multiple-character phrases in Chinese. When I type in pinyin, ibus seems to want me to select one Chinese character at a time rather than letting me type the pinyin for two or more Chinese characters and guessing the word or phrase I want.

At first I assumed that it was the input method I'm using--py (&#25340;ALL). But none of the other pinyin-based methods (tonepy and pinyin) seem to allow this, either.

Scim seemed to do this by default, but I can't figure out how to configure ibus to work this way. Any help would be greatly appreciated.

---

### Post by Irihapeti on 2009-11-09
It sounds like you need to install ibus-pinyin, which is a method fairly similar to scim-pinyin.

Either use synaptic (or equivalent if you're using KDE) or in a terminal:

```
sudo apt-get install ibus-pinyin
```

I'm not sure if ibus-pinyin allows you to save user-defined phrases. I haven't used it very much.

---

### Post by contents on 2009-11-10
Thanks for your reply. I've already got ibus-pinyin installed, but the behavior is just as I described before. There is an input choice just called "pinyin" in the preferences of ibus, but that seems to be for inputting the pinyin Roman letters with tone marks (luóm&#462; p&#299;ny&#299;n).

I must have something configured incorrectly. Do you or anyone else have any other clues as to what I could check next?

---

### Post by Irihapeti on 2009-11-10
The "pinyin" you mention is part of the ibus-m17n package. ibus-pinyin is called "PinYin" - yes, confusing. I've attached a couple of screenshots to show you the one you need to activate.

If you can't find it in your list of options, then either it's not installed or you need to log out and in again (or reboot).

---

### Post by contents on 2009-11-11
Hmm--this seems quite odd. I don't have PinYin in my list of options, but ibus-pinyin is installed. I have restarted several times. Do you think I might be missing some other ibus package?

---

### Post by Irihapeti on 2009-11-11
I think that if you were missing another package, apt-get or Synaptic would have told you. More likely, some configuration file is missing or confused.

The only thing I can suggest is to remove ibus-pinyin completely (or purge if you prefer to use the terminal), logout and in again, and then reinstall it. This will remove the ibus-table and ibus-m17n packages, but you don't need them to use ibus-pinyin, and you can reinstall them later if you want.

Then set up ibus again. You should only see Chinese - PinYin in the list of choices.

Edit: I meant to say, remove ibus AND ibus-pinyin completely.

---

