---
title: "Keyboard layouts/xmodmap - am i doing something bad or is this a bug?"
date: 2010-08-30
forum: General Help
---

### Post by Zorgoth on 2010-08-30
I am using the following script in my startup applications to set Menu to change keyboard layout while pressed and Insert to switch layouts.

bash -c "sleep 5 && xmodmap -e 'keycode 135=Mode_switch' && xmodmap -e 'keycode 118=ISO_Next_Group'"

(the sleep 5 is because doing it immediately seems to not always work)

Those key names (Mode_switch and ISO_Next_Group) I got by using the more limited GNOME keyboard layout options and using xev to figure out what keys it was using.

I am having horrible problems with this however.  Sometimes when a new window opens the keyboard layout changes (globally) without me pressing Insert, and this is not indicated by the keyboard layout indicator.

For example I use Polish, Greek, and Russian layouts in that order and sometimes the layout will arbitrarily switch to Greek - at this point the indicator will still think the layout is Polish and I can switch back to Polish by pressing Insert twice, but the keyboard layout indicator will on these two Insert presses change from Polish to Greek, then Greek to Russian, and so when my keyboard layout is Polish again, it will say 'Rus' rather than 'Pol.'

Sometimes after this bug has been going on for a while I lose all my compiz shortcuts (Alt-Tab, Ctrl-Alt-Left, etc) until I log out.

---

