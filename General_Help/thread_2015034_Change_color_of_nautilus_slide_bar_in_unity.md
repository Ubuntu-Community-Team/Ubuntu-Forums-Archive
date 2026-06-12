---
title: "Change color of nautilus slide bar in unity"
date: 2012-07-02
forum: General Help
---

### Post by O2Blevel on 2012-07-02
Is it possible to change the color of the slide bar in the unity DE, ubuntu 12.04. I see there are ways to do it with the gnome desktop but haven't found any for unity.

---

### Post by msammels on 2012-07-03
What do you mean by slide bar? Do you mean the scrollbar in windows? If so do the following in a terminal shell:

```
sudo nano /usr/share/themes/Ambiance/gtk-2.0/gtkrc
```

Once this document has opened look below in the curly braces andchange the bg[SOMETHING] lines to look like:

```
bg[NORMAL] = @selected_bg_color
bg[PRELIGHT] = shade (1.04, @selected_bg_color)

bg[ACTIVE] = shade (0.96, @selected_bg_color)
```

Or look at the colors declared in line 1 of the file and select the one you prefer. To update the looks, in System settings/Appearance, change the theme to another one and back to Ambiance.

---

### Post by O2Blevel on 2012-07-03
I changed those lines under the section 'style "scrollbar' = "button" {' but it didn't change the scrollbar color in nautilus.

It's my understanding that unity is controlled by gtk-3.0. Is that not correct, at any rate I looked in the usr/share/themes/gtk-3.0 folder but I didn't see any way to change the scrollbar.

I've used gnome-color-chooser to change the scrollbars in my applications but it didn't affect nautilus, gedit or gnome-terminal. Nautilus is my primary concern as I have a very difficult time dealing with the lack of contrast.

---

### Post by msammels on 2012-07-03
Hey O2,

Maybe [this](http://ubuntuforums.org/showthread.php?p=11516019) will help.

---

### Post by vasa1 on 2012-07-03
You can see this:
[http://ubuntuforums.org/showthread.php?p=11517671#post11517671](http://ubuntuforums.org/showthread.php?p=11517671#post11517671)

(Gnome Color Chooser is great for gtk2 apps but doesn't affect gtk3 apps.)

---

### Post by vasa1 on 2012-07-03
> **O2Blevel said:**
> ... Nautilus is my primary concern as I have a very difficult time dealing with the lack of contrast.

Could you give a little more detail about which theme you are using and perhaps put up an image of the area in which you would like contrast enhanced?

And, if you can, you may want to change "slide bar" to "scrollbar" in your title. If you are willing but can't, you could ask a mod via the report button near the bottom left of each post.

And have you dispensed with the "overlay" scrollbar? You haven't said anything about that.

My understanding is that the default _is_ the overlay scrollbar in things like nautilus, gedit and the terminal.

Is that what is troubling you and what you call the slider?

---

### Post by O2Blevel on 2012-07-04
> **vasa1 said:**
> Could you give a little more detail about which theme you are using and perhaps put up an image of the area in which you would like contrast enhanced?

And, if you can, you may want to change "slide bar" to "scrollbar" in your title. If you are willing but can't, you could ask a mod via the report button near the bottom left of each post.

And have you dispensed with the "overlay" scrollbar? You haven't said anything about that.

My understanding is that the default _is_ the overlay scrollbar in things like nautilus, gedit and the terminal.

Is that what is troubling you and what you call the slider?

Thanks for the quick response. I found it easier to install a new theme, not perfect but better than before. I just don't understand why the installed themes have such low contrast between the scrollbar and background.

---

### Post by vasa1 on 2012-07-04
> **O2Blevel said:**
> Thanks for the quick response. I found it easier to install a new theme, not perfect but better than before. I just don't understand why the installed themes have such low contrast between the scrollbar and background.
But you haven't answered my question. Are you using the conventional scrollbars or the overlay?

BTW, it's possible to increase the contrast for anything but the Chrome/Chromium browser. But if you want help you'll have to be a bit more specific about what the problem is :)

---

### Post by O2Blevel on 2012-07-04
> **vasa1 said:**
> But you haven't answered my question. Are you using the conventional scrollbars or the overlay?

BTW, it's possible to increase the contrast for anything but the Chrome/Chromium browser. But if you want help you'll have to be a bit more specific about what the problem is :)

I'm using the conventional scrollbar not the overlay.

The color of the scrollbar and the background are so similar I don't think increasing the contrast would help. The theme I downloaded has a blue scrollbar against the off-white background, a world of difference. No more 3 or 4 tries to grab the scrollbar.:D

---

### Post by grey1beard on 2013-03-18
My other half has a similar problem with the low contrast you mentioned.
Can you tell me what theme it was that you downloaded and found to be an improvement ?
Many thanks,
John

---

### Post by Kopkins on 2013-03-18
in /usr/share/themes/name-of-theme/gtk-2.0/gtkrc

There is a line in that file like this ```

colorize_scrollbar = FALSE
```

If you change that to TRUE it will make your scrollbars Ubuntu orange. 

The default theme is Ambiance so it would be in /usr/share/themes/Ambiance/gtk-2.0/gtkrc

The easiest way for you is probably using gedit.

```
gksudo gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc

```

Then search for colorize_scrollbar and change FALSE to TRUE.

Good luck,

Kopkins

---

