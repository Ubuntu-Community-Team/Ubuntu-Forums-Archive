---
title: "Missing Menu Icons in Lucid with NO Option to Restore Them? Seriouslty?"
date: 2010-06-08
forum: General Help
---

### Post by ALIENDUDE5300 on 2010-06-08
This probably doesn't matter at all to any of you, and I'd like to apologize in advance for ranting, but it *really* irritates me that in Ubuntu Lucid not all the icons in the menus on the panel at the top of the screen are there any more... how do I get those back? I really miss my bookmarks icon, and the icons in the system menu. In Karmic, at least there was an option to show the menu icons, but now, that option isn't there any more -- who's stupid decision was that? I don't care if the icons are there by default, I just want the choice of whether or not they are displayed. :(

---

### Post by ALIENDUDE5300 on 2010-06-08
I managed to find a solution [here]("http://brainstorm.ubuntu.com/idea/23991/"), but I still believe this option should be enabled by default. For those who are interested, try this code:
```
gconftool-2 -s -t boolean /desktop/gnome/interface/buttons_have_icons true
gconftool-2 -s -t boolean /desktop/gnome/interface/menus_have_icons true 
```

Edit: Yes I realize "Seriously" is spelled wrong in the title. I typed this in a hurry, and didn't really look over it that much. It won't let me edit it.

---

