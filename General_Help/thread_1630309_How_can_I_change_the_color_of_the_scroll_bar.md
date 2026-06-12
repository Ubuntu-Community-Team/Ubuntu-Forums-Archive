---
title: "How can I change the color of the scroll bar?"
date: 2010-11-25
forum: General Help
---

### Post by castlefox on 2010-11-25
How can I change the color of the scroll bar?

I am using 10.04 ubuntu.  I want to keep the same basic theme but the scroll bar is way too hard to see.    I want to change to the same color as the orange X to close all the windows are. 

Thank you anyone can help me.

---

### Post by hhh on 2010-11-25
You need to edit a color hex code in the /gtk-2.0/gtkrc file of the theme you're using, located in /usr/share/themes (or ~/.themes). These files differ greatly from theme to theme, so I can't tell you which line to edit. Sometimes there isn't a hex code either, but a reference to a hex code of another theme element, as in...```
style "scrollbar" {
    fg[NORMAL] = @text_color
    fg[ACTIVE] = darker (@text_color)
    fg[PRELIGHT] = shade (1.1, @text_color)
    fg[INSENSITIVE] = darker (@bg_color)
#	bg[NORMAL] = shade (.9, @bg_color)
#	bg[INSENSITIVE] = @bg_color
#	bg[PRELIGHT] = shade (1.18, @bg_color)
#	bg[ACTIVE] = shade (0.85, @bg_color)
#	bg[SELECTED] = shade (.4, @bg_color)
#	
	engine "murrine" 
    {
		contrast = 0.4
		gradient_shades = { 0.91, 0.96, 0.96, 0.91 }
		roundness = 0
	}
}
```

What theme are you using? I could take a look for you. A screenshot would help too, as I'm on Xfce and my close buttons will look different.

---

### Post by stinkeye on 2010-11-25
**gnome-color-chooser** in the "specfic" tab allows you to change the color (and width) of the scrollbar.

---

### Post by hhh on 2010-11-25
> **stinkeye said:**
> **gnome-color-chooser** in the "specfic" tab allows you to change the color of the scrollbar.
*facepalm* I forgot all about that. A million times easier.

---

### Post by stinkeye on 2010-11-25
#-o

---

