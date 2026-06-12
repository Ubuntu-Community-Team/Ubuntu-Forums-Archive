---
title: "How do I type the copyright sign (c)?"
date: 2010-07-04
forum: General Help
---

### Post by David Deu on 2010-07-04
Hi,
Is there any shortcut on keyboard to make this sign: © ? 
I know that in Office it appears automatically by typing "(c)", but what is about any other application?

---

### Post by sisco311 on 2010-07-04
Ctrl+Shift+u a9

EDIT:
[uhelp]community/ComposeKey[/uhelp]
[http://en.wikipedia.org/wiki/List_of_Unicode_characters](http://en.wikipedia.org/wiki/List_of_Unicode_characters)

---

### Post by Rubi1200 on 2010-07-04
Ctrl + Shift + U; then 00A9

oops; see above

---

### Post by ajgreeny on 2010-07-04
There is a mass of different unicode characters, including lots of fractions available to you as well, so do a google search on "unicode characters" and I'm sure you'll find them.

---

### Post by The Cog on 2010-07-04
AltGr-Shift-C does it as well for me (UK keyboard layout).

---

### Post by simosx on 2010-07-04
> **David Deu said:**
> Hi,
Is there any shortcut on keyboard to make this sign: © ? 
I know that in Office it appears automatically by typing "(c)", but what is about any other application?

There are several ways, as already mentioned.

1. The universal way where you type the Unicode ID of the character,

Ctrl+Shift+a9+SPACE = ©

(Works for GNOME applications, including OpenOffice.org and Firefox)

2. Using compose sequences. These are special mnemonics. See the link in the post above on Compose. Here, you need to enable the Compose key, then you press

Compose + 0 + c = ©
Compose + c + 0 = ©

These are quite self-explaining, © is a c in a 0.

These work in all Ubuntu applications.

3. Select a keyboard layouts that offers this character. The default GB layout has the copyright key, at AltGr+ C = ©
If you run 
grep copyright /usr/share/X11/xkb/symbols/*
you can see what's the case with other layouts.
From the results, the 'us' layout has the copyright symbol if you select either the US International with Dead keys or the Macintosh layouts.

These work in all Ubuntu applications.

4. In OpenOffice.org, you can type (c), press space and you get ©.

---

### Post by David Deu on 2010-07-04
An interesting thing:
the combination of the unicode keys works very well and I succeed to type a few symbols I was looking for, but what I don't understand is why I it doesn't work in OpenOffice? nothing happens after pressing the specific keys.
Is it something to set or what?

Thanks,
David

---

### Post by David Deu on 2010-07-05
Got it! 
you've to press the "space" after the keys combinations.

---

