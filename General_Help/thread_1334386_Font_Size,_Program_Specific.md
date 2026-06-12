---
title: "Font Size, Program Specific???"
date: 2009-11-22
forum: General Help
---

### Post by webbdawg on 2009-11-22
I have edited the system preferences to get fonts a little bigger so they are readable.

But in Thunderbird (mail) only the actual System Window fonts are changed. All the folder listings and actual incoming mail pane fonts are still small.

I have tried in Thunderbird (restarted each time) and in the system setting s to play with settings but these fonts just stay as they are.

Any thoughts on this???

PS: There are other programs too but I figure if I fix Thunderbird the others will be easy to figure out.

Thanks
Dave

---

### Post by Zorael on 2009-11-22
And there are no ways in Thunderbird's own settings to change what fonts it will use?

In the case of Firefox and Thunderbird, you can also create/modify the **userchrome.css** and **usercontent.css** files if you want to modify the look of stuff. Googling those names (in the context of firebird) comes up with quite a few guides, such as [this one](http://eriwen.com/css/tweaking-thunderbirds-chrome/).

The only other alternative I know of is to make a fontconfig rule (in ~/.fonts.conf) where you catch the call for the font (and optionally size etc) and change it to what you want it to be. It would, however, affect all occurences of the font in all apps, so if it's "Arial 12" and you make it be "Arial 16", stuff will look weird on you eventually. You would also need to know what font is being used.

---

### Post by webbdawg on 2009-11-22
Thunderbird has font setting for the creation and viewing of emails.

I am talking about the folder pane and the email listing pane, not the email preview pane.

These should be controlled by the system window settings. Though I am not sure.

I will look at Dophin file manager and see how the panes there look.

Thanks though
Dave

---

### Post by Zorael on 2009-11-23
I'm not sure to what folder pane you're referring, I'm afraid. As long as you've set KDE up to use the QtCurve GTK+ style, GTK apps should listen to your KDE font settings. If it's a font that's been explicitly defined in the code, I think usercontent.css is the right approach to change it.

If you can change it under GNOME, then I'm wrong, and there's something missing in KDE's GTK styling.

---

### Post by webbdawg on 2009-11-26
Problem solved.

I installed the Nvidia driver and the fonts look normal now.

Amazing ain't it

---

