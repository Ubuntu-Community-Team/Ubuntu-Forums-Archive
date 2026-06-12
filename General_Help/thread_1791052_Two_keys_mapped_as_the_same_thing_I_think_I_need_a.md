---
title: "Two keys mapped as the same thing? I think I need a drink now"
date: 2011-06-26
forum: General Help
---

### Post by thatoneshadykid on 2011-06-26
After pissing around with Kubuntu all evening, I wish I had hair to pull out in screaming frustration. After trying everything from Xbindkeys to animal sacrifices and voodoo spells to get my multimedia keys working, I now find that both the Windows key and the End key are mapped as F14. Problem is that it's the End key opening the K Menu, not the Windows key.

How can two keys get mapped as the same thing?! And how do I get the End key back to just the End key? I'm close to calling it quits on Linux and putting Windows back on my laptop.

---

### Post by enimeizoo on 2011-07-29
Well, if you are still here, xmodmap and xev would probably do more than animal sacrifices. Depending on the animals, though.
Didn't the vodoo spells have any effect?

This powerfull spell will give you your whole keyboard mapping, you might want to inhibit it with grep a bit, or your home could be blown.
```
xmodmap -pke
```

---

