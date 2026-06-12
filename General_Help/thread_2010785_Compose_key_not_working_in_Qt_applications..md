---
title: "Compose key not working in Qt applications."
date: 2012-06-26
forum: General Help
---

### Post by Woegjiub on 2012-06-26
I have the compose key set, and it works under unity in most applications, except for Qt applications.

I tried installing KDE, and setting it in KDE's system settings, but apps like konsole and anki are still not recognising the compose key.

I have it set to caps-lock, and when that key is struck in these apps, they do not receive capitalised input, so I know that it is treating it as special, but I can not for the life of me figure out why it is that they are not allowing the recognition of the modifiers to allow ß,ä, etc to be typed.

Edit:
Turns out, ibus-Qt4 is not installed by default as a dependency of ibus, so if one enables CJK input or similar, the compose key stops working. Interesting.

---

