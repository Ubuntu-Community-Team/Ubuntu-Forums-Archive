---
title: "How can I change the font in all Applications except for Nautilus?"
date: 2011-06-17
forum: General Help
---

### Post by inameiname on 2011-06-17
I have recently decided on leaving the default Ubuntu font behind for something different.

Going to Main Menu > System > Preferences > Appearance and clicking on the Fonts tab I am able to change the Application font, Desktop font, and Windows title font from Ubuntu to my new choice of fonts.

It looks great everywhere but Nautilus. It is pretty on the menu, taskbar, desktop, and everything else, but not in Nautilus. Too hard to read and type of the filenames and folders.

As such, I'm looking for a way to change it everywhere else, using the methods above, but not in Nautilus. Anybody know how?

Similar, I was able to find this posting, and using the method described below, it merely allows you to change the desktop icons, not the rest of Nautilus, which you could do using the method I mentioned above anyway.: [http://www.linuxquestions.org/questions/linux-newbie-8/change-fonts-in-nautilus-without-affecting-other-apps-desktop-817633/:](http://www.linuxquestions.org/questions/linux-newbie-8/change-fonts-in-nautilus-without-affecting-other-apps-desktop-817633/:)

> 
run gconf Applications->System Tools->Configuration Editor
go to apps->nautilus->preferences and look for the desktop_font  entry change this to something else and see if that is what you want


---

### Post by inameiname on 2011-06-17
I've found another way than the Configuration Editor to resolve my issue, adding stuff to a gtkrc-2.0 file inside my home folder.

So far, I've been able to play around with doing this and change just the desktop icon color, the clock on the taskbar's color and font, and quite interestingly, the taskbar and main menu items using the following code:

```

style "my_font"
{
font_name = "Schoolbell Bold 11"
}
widget "*" style "my_font"
```It works, and I like that it changes everything like choosing Main Menu > System > Preferences > Appearance and clicking on the Fonts tab > Applications Font to the one I want, but not the text inside Firefox, gnome-terminal, configuration-editor, etc (which is nice because its hard to read on those things) or in other parts. Unfortunately, this is still not what I want because it does change the font in Nautilus. :( But I'm close.

---

### Post by inameiname on 2011-06-18
Bump...

So far, I have been unsuccessful at figuring out how to change only Nautilus (not the desktop) to the font I want.

---

### Post by AlphaLexman on 2011-06-18
Unless you are using gnome3 or unity (I'm not familiar with these), Nautilus **IS** the desktop.
AFAIK, your request is **NOT** possible.

---

### Post by inameiname on 2011-06-18
It is, yes, but not when it comes to the font settings for some reason. For instance, if you go the Appearance settings and change the desktop font to something, only the actual desktop icon font changes, not that inside Nautilus File Manager. Thus, a sign its not exactly the same setting, hence my issue. 

Oh well. I was just hoping there is a way to manually change a specific Application to a different font than what is set for Application font in the Appearance menu.

---

