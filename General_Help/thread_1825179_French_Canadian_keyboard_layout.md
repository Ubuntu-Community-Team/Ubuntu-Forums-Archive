---
title: "French Canadian keyboard layout"
date: 2011-08-14
forum: General Help
---

### Post by ClickHeRe on 2011-08-14
How can I get my French (Canada) - Canadian French layout on Xubuntu the same way it behaves on Windows?

That is to get the French accented characters I need to press 2 keys

USA - International (with dead keys) is the closest I have found but not quite it

Pressing the key with " + ´ with e should give è and not é
Same as above with a instead of e giving à instead of á
Key with ? + / should directly give é
etc...

Tried all the combinations of keyboards and not one can give me the same as what I have on Windows.

Thanks

---

### Post by ClickHeRe on 2011-08-24
After fiddling to write my own xmodmap file and such things, I found out the solution at least on Xubuntu.

Looking at the keyboard definitions under /usr/share/X11/xkb/symbols/ca which end up in the Keyboard list, I found that the line representing Canada below in the tree of available keyboards is in fact itself a keyboard config (highly confusion and non intuitive) instead of just a category regrouping the others below it.

Keyboard Tree under Canada

Canada <-- This is the Canadian French keyboard definition as found in the file above
- English
- French Dvorak
- French (legacy)
...

Selected it and I now have the same behaviour as the one on Windows.

Hope this helps people in the future.

---

### Post by zeroforme on 2012-10-16
Here is a way to get the **French (Switzerland)** keyboard layout on xubuntu:

go to: Settings->Settings Manager->Keyboard->Layout

and *Add* the "**German (Switzerland)**" keyboard layout since the "French (Switzerland)" is a variant from the first one.

---

### Post by vinylfil on 2013-01-10
bit of an old thread but I had this problem and this [http://www.computeractive.co.uk/ca/pc-help/1933825/add-accents-office-writer-text-editor](http://www.computeractive.co.uk/ca/pc-help/1933825/add-accents-office-writer-text-editor) thread sorted it.

---

