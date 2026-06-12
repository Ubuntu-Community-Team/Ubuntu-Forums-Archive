---
title: "console: keyboard ok &gt; after logging in to gui: keyboard flaky"
date: 2006-06-25
forum: General Help
---

### Post by takayuki on 2006-06-25
hi,

i did a server install, then installed fluxbox and xfce4.  everything is grooy, *but* in the gui, certain keys on my japanese keyboard aren't mapped correctly.  for example the right bracket is a \.

the crazy part is that in console mode, the keyboard is mapped correctly.

the same keyboard mapping problem happens in fluxbox and xfce4.

yes, i've tried every possible xorg.conf configuration for japanese keyboards.  here's what i've got, which doesn't work.  i even changed keyboards (japanese) and got the same issue.

Section "Input Device"
     Identifier    "Generic Keyboard"
     Driver        "kbd"
     Option        "CoreKeyboard"     "xorg"
     Option        "XkbRules"           "xorg"
     Option        "XkbModel"           "pc105"
     Option        "XkbLayout"          "jp"
     Option        "XkbVariant"         "jp106"

any thought greatly appreciated,

takayuki

---

