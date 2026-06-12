---
title: "Elementary theme and Ubuntu Maverick"
date: 2010-10-08
forum: General Help
---

### Post by Budoc on 2010-10-08
Hi,

Apologies if I've not posted this in the correct section. I wasn't sure whether to post this in the Maverick testing forum, or the general help forum as my questions relate to a theme that is installable from a non-default repository.

Anyway, I've made a fresh install of 10.10RC today, after encountering too many problems with Lucid. I've mostly figured everything out now, except a few things with the Elementary theme which is available from [https://launchpad.net/~elementaryart/+archive/ppa](https://launchpad.net/~elementaryart/+archive/ppa)

The first thing that I've noticed is that my scroll bars no longer have clickable arrows on them so that I can scroll by small increments. I now am only able to scroll by dragging the scroll bar to where I want it, or by pressing page up/page down. Does anybody know whether this is the intended default behaviour, or has something gone wrong?

The second issue that I've found is that the selectable statuses in the indicator applet session for pidgin appear to be the ugly clearlooks ones. This didn't happen in Lucid. Is this an intended change, or have I got something missing on my system?

The elementary packages that I have got installed are: elementary-theme, elementary-icon-theme and elementary-wallpapers. I've attached a screen shot below of the ugly clearlooks status icons in the indicator applet session.

Thanks in advance!

---

### Post by gordintoronto on 2010-10-08
If the theme has caused this grief, why don't you remove it?

---

### Post by Budoc on 2010-10-08
> **gordintoronto said:**
> If the theme has caused this grief, why don't you remove it?

I am free to remove it, should I wish to. I quite like the theme, as it is easy on my eyes. As it is quite a popular theme, I am posting here to see whether anybody else has noticed these issues.

---

### Post by Budoc on 2010-10-13
Anybody?

---

### Post by PJSingh5000 on 2010-10-30
Budoc,

I can certainly appreciate your dilemma.  The Elementary theme is *indeed* quite nice.  Dan Rabbit on Deviantart mentioned that the intention of the thin/small scroll bar and slider in Elementary is to provide a visual queue as to your position in a document, and so it was not intended to be used for navigation.

Although I'm sure many users appreciate the simplicity of the scroll bar approach the talented folks at Elementary have taken, some of us *actually do use* the scroll bar.  As one person on another forum pointed out, the scroll bar is very useful to grab and quickly slide to a section of a long document, without having to rotate your mouse's scroll wheel numerous times.

In addition to the scroll bar being very small and thin, the scroll bar is completely missing in OpenOffice.org, while using the Elementary theme.  (Dan stipulated that this is an OpenOfffice bug).

Nevertheless, for those of us who want a more substantial scroll bar, we are free to modify our code to suit our needs-- which is the beauty of OpenSource!

Here is what I did to remedy both situations...

Edit the gtkrc file for the elementary theme.
```
$ gksudo gedit /usr/share/themes/elementary/gtk-2.0/gtkrc
```

Replace:
```
GtkRange		::slider-width				= 8
```
With:
```
GtkRange		::slider-width				= 10
```

Replace:
```
GtkScrollbar		::has-backward-stepper 			= 0
GtkScrollbar		::has-forward-stepper			= 0
```
		
With:
```
GtkScrollbar		::has-backward-stepper 			= 1
GtkScrollbar		::has-forward-stepper			= 1
```
		
Replace:
```
GtkScrolledWindow	::scrollbars-within-bevel		= 1
```
With:
```
GtkScrolledWindow	::scrollbars-within-bevel		= 0
```

Finally, replace the _entire_ scroll bar definition:
```
style "murrine-scrollbar"
{
	.
	.
	.
}
```

With:
```
style "murrine-scrollbar"
{
	
	fg[PRELIGHT]				= @selected_fg_color
	fg[SELECTED]				= @selected_fg_color
	fg[ACTIVE]				= @fg_color
	fg[INSENSITIVE]				= darker (@bg_color)

	bg[SELECTED]				= shade (0.90, @selected_bg_color)

	engine "murrine"
	{
		contrast			= 0.5
		roundness			= 3
		lightborderstyle		= 1
	}
}
```

Save gtkrc and exit gedit.  Now log out, and log back in.  You should have usable scroll bars that match the Elementary color scheme and fit reasonably well with the theme's concept of minimalism and simplicity.  Also OpenOffice.org documents will now have working scroll bars.

I have attached a couple of screen shots so you can see the results.

---

### Post by Budoc on 2010-10-31
Thanks very much **PJSingh5000**! I'll give it a go. I wasn't sure if the missing scroll arrows were a design decision, or just a bug. Either way, I now know how to customize it myself, thanks to your very useful instructions.

Do you have any idea why I am getting clearlooks-looking icons in the indicator applet session? Is this a problem with the elementary-icon-theme package supplied with Maverick? If I change the icon theme used to anything but elementary or elementary-monochrome, the icons used in the indicator applet session menu change. Is the elementary-icon-theme package in Maverick missing some icons?

Attached is a picture of an open indicator applet session with elementary-monochrome icons. The icon for invisible on the panel is fine (a light grey speech bubble), but this doesn't match with the drop down menu (a silver pentagon). In Lucid, the icons in the drop down menu matched the icons that were displayed on the panel.

---

### Post by PJSingh5000 on 2010-11-01
Budoc,

You're welcome.

I don't know why the icon's are from ClearLooks.  My guess is that elementary does not have icons for these (????).  I used to use Kubuntu Lucid, so I didn't even know it was different in Ubuntu Maverick vs. Lucid.

---

### Post by gandaran on 2010-11-01
> **PJSingh5000 said:**
> Budoc,

I can certainly appreciate your dilemma.  The Elementary theme is *indeed* quite nice.  Dan Rabbit on Deviantart mentioned that the intention of the thin/small scroll bar and slider in Elementary is to provide a visual queue as to your position in a document, and so it was not intended to be used for navigation.

Although I'm sure many users appreciate the simplicity of the scroll bar approach the talented folks at Elementary have taken, some of us *actually do use* the scroll bar.  As one person on another forum pointed out, the scroll bar is very useful to grab and quickly slide to a section of a long document, without having to rotate your mouse's scroll wheel numerous times.

In addition to the scroll bar being very small and thin, the scroll bar is completely missing in OpenOffice.org, while using the Elementary theme.  (Dan stipulated that this is an OpenOfffice bug).

Nevertheless, for those of us who want a more substantial scroll bar, we are free to modify our code to suit our needs-- which is the beauty of OpenSource!

Here is what I did to remedy both situations...

Edit the gtkrc file for the elementary theme.
```
$ gksudo gedit /usr/share/themes/elementary/gtk-2.0/gtkrc
```

Replace:
```
GtkRange		::slider-width				= 8
```
With:
```
GtkRange		::slider-width				= 10
```

Replace:
```
GtkScrollbar		::has-backward-stepper 			= 0
GtkScrollbar		::has-forward-stepper			= 0
```
		
With:
```
GtkScrollbar		::has-backward-stepper 			= 1
GtkScrollbar		::has-forward-stepper			= 1
```
		
Replace:
```
GtkScrolledWindow	::scrollbars-within-bevel		= 1
```
With:
```
GtkScrolledWindow	::scrollbars-within-bevel		= 0
```

Finally, replace the _entire_ scroll bar definition:
```
style "murrine-scrollbar"
{
	.
	.
	.
}
```

With:
```
style "murrine-scrollbar"
{
	
	fg[PRELIGHT]				= @selected_fg_color
	fg[SELECTED]				= @selected_fg_color
	fg[ACTIVE]				= @fg_color
	fg[INSENSITIVE]				= darker (@bg_color)

	bg[SELECTED]				= shade (0.90, @selected_bg_color)

	engine "murrine"
	{
		contrast			= 0.5
		roundness			= 3
		lightborderstyle		= 1
	}
}
```

Save gtkrc and exit gedit.  Now log out, and log back in.  You should have usable scroll bars that match the Elementary color scheme and fit reasonably well with the theme's concept of minimalism and simplicity.  Also OpenOffice.org documents will now have working scroll bars.

I have attached a couple of screen shots so you can see the results.
thank you!
I wondered why such a nice theme had s**t scroll bars!
now it is truly a beautiful theme.

---

### Post by rybajz on 2010-11-04
Great. It really fixed my OO problem.:guitar:

---

### Post by Budoc on 2010-11-27
I finally solved my icons problem!

It turns out that the version of elementary-icon-theme in the repos for Maverick (2.4-0ubuntu1) has missing icons. I don't believe that the older version in Lucid had this problem.

First I uninstalled the icon theme:
```
sudo aptitude remove elementary-icon-theme
```

Then I went [here]("http://danrabbit.deviantart.com/art/elementary-Icons-65437279") and downloaded the latest set of elementary icons.

I extracted the elementary and elementary-mono-dark folders, and then copied them into ~/.icons. Now, when I select the elementary theme in appearances, I get a full set of icons in my indicator applet session menu.

---

### Post by PJSingh5000 on 2010-12-01
Budoc,

Thanks for the tip on correcting the outdated elementary icons.

Instead of removing elementary-icon-theme, I downloaded the version you suggested ([http://danrabbit.deviantart.com/art/elementary-Icons-65437279](http://danrabbit.deviantart.com/art/elementary-Icons-65437279)), and simply copied the extracted elementary folder on top of the existing /usr/share/icons/elementary folder.  I also copied the elementary-mono-dark folder to /usr/share/icons/.

This was definitely an improvement for the Indicator Applet Session drop-down.

However, I noticed that when I selected the elementary dark icons, the Indicator Applet Session drop-down was still using the monochrome icons.  It seems that this newer version of the icon set is also missing some icons or links.

In case anyone else runs into this problem, I was able to resolve it by creating links to the correct "dark" icons.
```

$ sudo ln -s /usr/share/icons/elementary-mono-dark/panel/22/user-available.svg /usr/share/icons/elementary-mono-dark/panel/22/user-available-panel.svg

$ sudo ln -s /usr/share/icons/elementary-mono-dark/panel/22/user-away.svg /usr/share/icons/elementary-mono-dark/panel/22/user-away-panel.svg

$ sudo ln -s /usr/share/icons/elementary-mono-dark/panel/22/user-busy.svg /usr/share/icons/elementary-mono-dark/panel/22/user-busy-panel.svg

$ sudo ln -s /usr/share/icons/elementary-mono-dark/panel/22/user-idle.svg /usr/share/icons/elementary-mono-dark/panel/22/user-idle-panel.svg

$ sudo ln -s /usr/share/icons/elementary-mono-dark/panel/22/user-offline.svg /usr/share/icons/elementary-mono-dark/panel/22/user-offline-panel.svg

```

Here is what it finally looks like...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177088&stc=1&d=1291186711[/IMG]

(There does not seem to be an elementary-mono-dark icon for the "user invisible" state).

---

### Post by 5ulo on 2010-12-05
> **PJSingh5000 said:**
> 
Finally, replace the _entire_ scroll bar definition:
```
style "murrine-scrollbar"
{
	.
	.
	.
}
```

With:
```
style "murrine-scrollbar"
{
	
	fg[PRELIGHT]				= @selected_fg_color
	fg[SELECTED]				= @selected_fg_color
	fg[ACTIVE]				= @fg_color
	fg[INSENSITIVE]				= darker (@bg_color)

	bg[SELECTED]				= shade (0.90, @selected_bg_color)

	engine "murrine"
	{
		contrast			= 0.5
		roundness			= 3
		lightborderstyle		= 1
	}
}
```


Why this? It works very well without this step. Or am I wrong?
But thank You for this fix!!!

---

### Post by santhust on 2011-01-12
> **PJSingh5000 said:**
> Budoc,

I can certainly appreciate your dilemma.  The Elementary theme is *indeed* quite nice.  Dan Rabbit on Deviantart mentioned that the intention of the thin/small scroll bar and slider in Elementary is to provide a visual queue as to your position in a document, and so it was not intended to be used for navigation.

Although I'm sure many users appreciate the simplicity of the scroll bar approach the talented folks at Elementary have taken, some of us *actually do use* the scroll bar.  As one person on another forum pointed out, the scroll bar is very useful to grab and quickly slide to a section of a long document, without having to rotate your mouse's scroll wheel numerous times.

In addition to the scroll bar being very small and thin, the scroll bar is completely missing in OpenOffice.org, while using the Elementary theme.  (Dan stipulated that this is an OpenOfffice bug).

Nevertheless, for those of us who want a more substantial scroll bar, we are free to modify our code to suit our needs-- which is the beauty of OpenSource!

Here is what I did to remedy both situations...

Edit the gtkrc file for the elementary theme.
```
$ gksudo gedit /usr/share/themes/elementary/gtk-2.0/gtkrc
```

Replace:
```
GtkRange		::slider-width				= 8
```
With:
```
GtkRange		::slider-width				= 10
```

Replace:
```
GtkScrollbar		::has-backward-stepper 			= 0
GtkScrollbar		::has-forward-stepper			= 0
```
		
With:
```
GtkScrollbar		::has-backward-stepper 			= 1
GtkScrollbar		::has-forward-stepper			= 1
```
		
Replace:
```
GtkScrolledWindow	::scrollbars-within-bevel		= 1
```
With:
```
GtkScrolledWindow	::scrollbars-within-bevel		= 0
```

Finally, replace the _entire_ scroll bar definition:
```
style "murrine-scrollbar"
{
	.
	.
	.
}
```

With:
```
style "murrine-scrollbar"
{
	
	fg[PRELIGHT]				= @selected_fg_color
	fg[SELECTED]				= @selected_fg_color
	fg[ACTIVE]				= @fg_color
	fg[INSENSITIVE]				= darker (@bg_color)

	bg[SELECTED]				= shade (0.90, @selected_bg_color)

	engine "murrine"
	{
		contrast			= 0.5
		roundness			= 3
		lightborderstyle		= 1
	}
}
```

Save gtkrc and exit gedit.  Now log out, and log back in.  You should have usable scroll bars that match the Elementary color scheme and fit reasonably well with the theme's concept of minimalism and simplicity.  Also OpenOffice.org documents will now have working scroll bars.

I have attached a couple of screen shots so you can see the results.
thanks very much :)

---

### Post by amalgamas on 2011-02-18
Thank you [santhust]("http://ubuntuforums.org/member.php?u=652338")!  Your suggestions solved this annoying problem that I have had since converting from ubuntu to pinguy.  I just inserted your suggestions into whatever was in the gtkrc file, and the result is perfect!

---

### Post by PJSingh5000 on 2011-03-13
Since I had added the elementary PPA ([http://ppa.launchpad.net/elementaryart/ppa/ubuntu](http://ppa.launchpad.net/elementaryart/ppa/ubuntu)) to my software sources, I just received an update to elementary which reverted the scroll bar fixes.  In the new version of elementary, "GtkScrollbar::slider-width" replaces "GtkRange::slider-width".

With this in mind, here are updates to my original post to "fix" the scroll bars.  Optionally you can make your progress bars and scroll bars match the blue menu item selection style.

**[COLOR="Blue"]OPEN OFFICE ELEMENTARY SCROLLBAR FIX[/COLOR]**

Edit gtkrc...
```

$ gksudo gedit /usr/share/themes/elementary/gtk-2.0/gtkrc

```

Replace the following values as shown.  (The default elementary values are shown as commented out)...
```

GtkScrollbar		::has-backward-stepper              = 1  [COLOR="SlateGray"]#0[/COLOR]
GtkScrollbar		::has-forward-stepper               = 1  [COLOR="SlateGray"]#0[/COLOR]
GtkScrollbar		::slider-width                      = 10 [COLOR="SlateGray"]#6[/COLOR]

```

**[COLOR="Blue"]MATCH SCROLL BAR  WITH MENU ITEM SELECTION STYLE (OPTIONAL)[/COLOR]**

Replace contents of "murrine-scrollbar" {...} with...
```

style "murrine-scrollbar"
{
	fg[PRELIGHT]     = @selected_fg_color
	fg[SELECTED]     = @selected_fg_color
	fg[ACTIVE]       = @fg_color
	fg[INSENSITIVE]  = darker (@bg_color)

	bg[SELECTED]     = shade (0.90, @selected_bg_color)

	engine "murrine"
	{
		contrast          = 0.8
		roundness         = 3
		lightborderstyle  = 1
	}
}
```

**[COLOR="Blue"]MATCH PROGRESS BAR WITH MENU ITEM SELECTION STYLE (OPTIONAL)[/COLOR]**

Replace contents of "murrine-progressbar" {...} with...
```

style "murrine-progressbar" = "murrine-thin"
{
	fg[PRELIGHT]     = @selected_fg_color
	fg[SELECTED]     = @selected_fg_color
	fg[ACTIVE]       = @fg_color
	fg[INSENSITIVE]  = darker (@bg_color)

	bg[SELECTED]     = shade (0.90, @selected_bg_color)

	engine "murrine"
	{
		contrast          = 0.8
		roundness         = 3
		lightborderstyle  = 1
	}
}
```

---

