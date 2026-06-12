---
title: "Change panel text to white?"
date: 2009-11-21
forum: General Help
---

### Post by Uncle Spellbinder on 2009-11-21
How can I change the panel text to white? 

I have several colors I'd like to use for the panel (as well as several images), all require white text.

Any help appreciated.

---

### Post by Uncle Spellbinder on 2009-11-21
Ideas, anyone?

---

### Post by VCoolio on 2009-11-21
Try this to change panel font color including applets / widgets:
Add the following to ~/.gtkrc-2.0 (create if it doesn't exist):

```
style "modpanel"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "modpanel"
widget "*PanelApplet*" style "modpanel"
widget "*fast-user-switch-applet*" style "modpanel"
```

Remember to undo this when you change themes ;). You can also put it in the gtkrc of your theme, but then make sure the widgets aren't defined to use a style twice.

---

### Post by Uncle Spellbinder on 2009-11-21
Thanks so much. Created the file, did *sudo killall gnome-panel* and all is great.

Thanks again!

---

### Post by Uncle Spellbinder on 2009-11-22
Applied the .gtkrc-2.0 above. Working well except for one thing. Is there any way to get the notification area icon and the window list icon to be black as well? See image below...

[[IMG]http://img163.imageshack.us/img163/9739/blackpanel.th.png[/IMG]](http://img163.imageshack.us/i/blackpanel.png/)

Direct link: [http://img163.imageshack.us/img163/9739/blackpanel.png](http://img163.imageshack.us/img163/9739/blackpanel.png)

Thanks in advance.

---

### Post by VCoolio on 2009-11-22
Could you post (a link to) the gtk theme you're using? I could take a look; I'm too unsure to start guessing and coding with try and error. Or if you know about gtk theming you could look in your gtk theme folder yourself and see if it's about the handle, and change the png or modify the gtkrc.

---

### Post by Uncle Spellbinder on 2009-11-23
It appears that way with any theme I use. Tried a bunch of different icon sets as well. No change. Currently though, in *change desktop background > theme*, I have controls: Industrial, window border: MetaGrip, icons: Gion

---

### Post by VCoolio on 2009-11-24
Edit: it seems this doesn't work; the panel stuff is always difficult. Sorry. 

Add the following to ~/.gtkrc-2.0 and create two small (eg. 5x11 and 11x5 pixel) images handle-h.png and handle-v.png (for horizontal and vertical, the latter being the one you need at the moment). If you don't want them in your home folder hide them by putting a . in front or put them where you want, but then modify the location in the code (at 'overlay_file') accordingly.

```
style "mypanelbuttons"
{
	engine "pixmap" {
    		image
    		{
      		function			= HANDLE
      		recolorable			= TRUE
      		overlay_file			= "handle-v.png"
      		overlay_stretch	= FALSE
      		orientation			= VERTICAL
    		}
    		image
    		{
      		function			= HANDLE
      		overlay_file			= "handle-h.png"
      		overlay_stretch 		= FALSE
     		orientation			= HORIZONTAL
   		}
	}
}

widget_class "*Panel*GtkToggleButton" 		style "mypanelbuttons"
widget "*.tasklist-button" 			style "mypanelbuttons"
widget_class "*PanelToplevel*Button" 		style "mypanelbuttons"
```

---

### Post by VCoolio on 2009-11-24
Ok, we need "PanelAppletFrame", so add this to ~/.gtkrc-2.0 and choose your desired color.


```
style "handle"
{
  bg[NORMAL] = "red"
}
class "PanelAppletFrame" style "handle"
```

[Credits]("http://ubuntuforums.org/showthread.php?t=1080704").

---

### Post by Uncle Spellbinder on 2009-11-24
> **VCoolio said:**
> Ok, we need "PanelAppletFrame", so add this to ~/.gtkrc-2.0 and choose your desired color.


```
style "handle"
{
  bg[NORMAL] = "red"
}
class "PanelAppletFrame" style "handle"
```

[Credits]("http://ubuntuforums.org/showthread.php?t=1080704").

Works great!  Thanks for your help. And the link!

;)

---

