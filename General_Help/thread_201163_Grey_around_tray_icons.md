---
title: "Grey around tray icons???"
date: 2006-06-21
forum: General Help
---

### Post by rekahsoft on 2006-06-21
I have Gaim 2.0 beta 3 installed on my system. There is gray around the gaim tray icons...every one...i have checked the icons using the GIMP and there is no gray around them. I recently installed Banshee 0.11.0-cvs and there is gray around that system tray icon as well. On the 0.10.0 version of banshee this did not happen. I checked the icon using the GIMP again and there is no gray around the icon. Is software putting the gray aroung the system tray icon???

---

### Post by Perfect Storm on 2006-06-21
It's because either the application is running with adminstration previledges or using .xpm as file.

---

### Post by z-vet on 2006-06-21
Same here: some GTK apps' icons have grey area around them (i use KDE, transparent panel). Anyone knows what's wrong with them?
Edit: You answered as i typed...thanks! :)

---

### Post by rekahsoft on 2006-06-21
What do you mean by> using .xpm as file..

---

### Post by Ramses de Norre on 2006-06-21
The program uses an .xpm file as icon, .xpm is an image filetype.

---

### Post by Perfect Storm on 2006-06-21
Some applications still uses .xpm format (god knows why) as eg. icons instead of using .png

[http://www.faqs.org/faqs/motif-faq/part5/section-30.html](http://www.faqs.org/faqs/motif-faq/part5/section-30.html)

[http://en.wikipedia.org/wiki/XPM_%28image_format%29](http://en.wikipedia.org/wiki/XPM_%28image_format%29)

---

### Post by rekahsoft on 2006-06-21
good to know...you learn something every day ;) 
Edit: I just checked and found that i am not running banshee as root and the icons are png's and i found one svg...there is still gray around the system tray icon. What is wrong? Note: i don't know which icon is being displayed in gnome panel.

---

### Post by rekahsoft on 2006-06-21
I think i found the problem...does anyone know if gray is put around apps that are a beta/alpha or a non official release? Because when i had Banshee 0.10.0 installed the icon was fine and when i installed Banshee 0.11.0-cvs it changed (they use the same icons).

---

### Post by panurge77 on 2006-06-21
Yes, I noticed this when changind to the new rhythmbox. I even copied the icon from the previous install and it's still gray ](*,)

---

### Post by xlyz on 2006-06-21
it's just the background set in gtk

---

### Post by rekahsoft on 2006-06-21
how do i change the background of the gtk? My gnome panel is clear so it is very obvios and it is slightly bothersome.

---

### Post by sisooktom on 2006-06-22
I've seen this before as well, but don't know how to fix it.  It is pretty unsightly when you use a transparent panel :/

---

### Post by rekahsoft on 2006-06-22
So there is no way to fix it? I have a transparent gnome panel so it is very obvious. Does anybody know how to fix it?

---

### Post by xlyz on 2006-06-22
edit the theme gtkrc (in /usr/share/themes) or override this setting using ~/.gtkrc and ~/.gtkrc-2.0

google to check the filenames are correct and how to do it

take care that changing it you will change the color of the background of the menu (or something like that, can't remember exactly)

---

### Post by rekahsoft on 2006-06-22
How do i do this? What is the name of the item i am looking to edit? Is it 'clearlooks-menu' ? Here is my gtkrc (from my Human theme):
```
# Ubuntu Human Colorscheme
#
# Authors:
# Richard Stellingwerff <remenic@gmail.com>
# Daniel Borgmann <daniel.borgmann@gmail.com>
# Billy Cantrell <bvcmdk@yahoo.com>
#
# Feel free to modify and share!


style "clearlooks-default"
{
	GtkButton      ::default_border    = { 0, 0, 0, 0 }
	GtkRange       ::trough_border     = 0
	GtkPaned       ::handle_size       = 6
	GtkRange       ::slider_width      = 15
	GtkRange       ::stepper_size      = 15

	GtkScrollbar   ::min_slider_length = 35
	GtkCheckButton ::indicator_size    = 14
	GtkMenuBar     ::internal-padding  = 0
	GtkTreeView    ::expander_size     = 14
	GtkExpander    ::expander_size     = 16
	GtkScale       ::slider-length     = 31
	# GtkToolbar     ::button-relief     = GTK_RELIEF_NORMAL
	# GtkMenuBar     ::shadow-type       = GTK_SHADOW_OUT
	# GtkScrollbar   ::has-secondary-forward-stepper = 1
	# GtkScrollbar   ::has-secondary-backward-stepper = 1

	GtkButton      ::child-displacement-x = 0
	GtkButton      ::child-displacement-y = 0

	xthickness = 1
	ythickness = 1

	GtkTreeView::odd_row_color = "#F5F2ED"
	GtkTreeView::even_row_color = "#FAF9F7"

	fg[NORMAL]        = "#101010"
	fg[PRELIGHT]      = "#000000"
	fg[ACTIVE]        = "#000000"
	fg[SELECTED]      = "#ffffff"
	fg[INSENSITIVE]   = "#B3AFAB"

	bg[NORMAL]        = "#efebe7"
	bg[PRELIGHT]      = "#f5f3f0"
	bg[ACTIVE]        = "#E1D9D1"
	bg[SELECTED]      = "#D6722D"
	bg[INSENSITIVE]   = "#EBE7E3"

	base[NORMAL]      = "#ffffff"
	base[PRELIGHT]    = "#ffffff"
	base[ACTIVE]      = "#E1D9D1"
	base[SELECTED]    = "#FFD799"
	base[INSENSITIVE] = "#EBE7E3"

	text[NORMAL]      = "#000000"
	text[PRELIGHT]    = "#000000"
	text[ACTIVE]      = "#000000"
	text[SELECTED]    = "#000000"
	text[INSENSITIVE] = "#B3AFAB"

	engine "ubuntulooks" 
	{
		menubarstyle      = 2       # 0 = flat, 1 = sunken, 2 = flat gradient
		menuitemstyle     = 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
		listviewitemstyle = 1       # 0 = flat, 1 = 3d-ish (gradient)
		progressbarstyle  = 1       # 0 = candy bar, 1 = fancy candy bar, 2 = flat
		animation         = TRUE
	}
}

# Evolution (and some deprecated widgets) use bg and fg for its listview instead of 
# base and text like they should, so we override it.
style "evolution-hack" = "clearlooks-default"
{	
	bg[ACTIVE]   = "#E1D9D1"
	bg[SELECTED] = "#FFD799"
	fg[ACTIVE]   = "#000000"
	fg[SELECTED] = "#000000"
}

# Bright orange highlights only for selected widgets
style "clearlooks-orange" = "clearlooks-default"
{
	bg[SELECTED] = "#FF6D0C"
}


style "clearlooks-wide" = "clearlooks-default"
{
	xthickness = 2
	ythickness = 2
}
style "clearlooks-wide-orange" = "clearlooks-wide"
{
	bg[SELECTED] = "#FF6D0C"
}

style "clearlooks-wider" = "clearlooks-default"
{
	xthickness = 3
	ythickness = 3
}
style "clearlooks-wider-orange" = "clearlooks-wider"
{
	bg[SELECTED] = "#FF6D0C"
}

style "clearlooks-button" = "clearlooks-wider-orange"
{
	bg[PRELIGHT] = "#f5f3f0"
	bg[ACTIVE]   = "#d9d3cc"
}

style "clearlooks-notebook" = "clearlooks-wide-orange"
{
	bg[NORMAL]      	= "#efebe5"
	bg[ACTIVE]      	= "#d0c8c1"
	bg[INSENSITIVE] 	= "#efebe5"
}

style "clearlooks-tasklist" = "clearlooks-default"
{
	xthickness = 5
	ythickness = 3
}

style "clearlooks-menu" = "clearlooks-default"
{
	xthickness = 2
	ythickness = 1
	bg[NORMAL] = "#f8f5f2"
}

style "clearlooks-menubar-item" = "clearlooks-button"
{
	fg[PRELIGHT] = "#000000"
}

style "clearlooks-menu-item" = "clearlooks-default"
{
	xthickness = 2
	ythickness = 3
	bg[SELECTED] = "#FFD799"
	fg[PRELIGHT] = "#000000"
	text[PRELIGHT] = "#000000"
}

style "clearlooks-tree" = "clearlooks-wide"
{
}

style "clearlooks-frame-title" = "clearlooks-default"
{
	fg[NORMAL] = "#404040"
}

style "clearlooks-tooltips" = "clearlooks-default"
{
	xthickness = 4
	ythickness = 4
	bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "clearlooks-progressbar" = "clearlooks-wide-orange"
{
	xthickness = 2
	ythickness = 2
	fg[PRELIGHT]  = "#ffffff"
}

style "clearlooks-combo" = "clearlooks-button"
{
}

style "clearlooks-check" = "clearlooks-button"
{
}

style "clearlooks-range" = "clearlooks-wide-orange"
{
}

style "metacity-frame" = "clearlooks-default"
{
	bg[SELECTED] = "#CC863E"
}

style "extra-view-widgets" = "clearlooks-default"
{
	bg[NORMAL] = "#F5C07F"
}


# widget styles
class "GtkWidget"      style "clearlooks-default"
class "GtkButton"      style "clearlooks-button"
class "GtkCombo"       style "clearlooks-button"
class "GtkRange"       style "clearlooks-range"
class "GtkFrame"       style "clearlooks-wide"
class "GtkMenu"        style "clearlooks-menu"
class "GtkEntry"       style "clearlooks-wider-orange"
class "GtkMenuItem"    style "clearlooks-menu-item"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
class "MetaFrames"     style "metacity-frame"
class "GtkWindow"      style "metacity-frame"

class "GtkCheckButton" style "clearlooks-check"
class "GtkRadioButton" style "clearlooks-check"

widget_class "*MenuItem.*" style "clearlooks-menu-item"
widget_class "*MenuItem.*ProgressBar*" style "clearlooks-default"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton"    style "clearlooks-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget "gtk-tooltips" style "clearlooks-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "clearlooks-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "clearlooks-notebook"

# these should really use base and text colors instead
widget_class "*GtkCTree*" style "evolution-hack"
widget_class "*GtkList*" style "evolution-hack"
widget_class "*GtkCList*" style "evolution-hack"
widget_class "*.ETree.*" style "evolution-hack"

widget "*.nautilus-extra-view-widget" style:highest "extra-view-widgets"
```

---

### Post by rekahsoft on 2006-06-23
Anybody? What do i edit to change the background of the icons? Also what is the hex color for transparent?

---

### Post by thx84 on 2006-08-30
in the section "clearlooks-default" spot this line

**bg[NORMAL]        = "#efebe7"** (

you've got to change it to the color of your wallpaper. for me it was easy since the wallpaper is white.

**bg[NORMAL]        = "#ffffff"** works fine for me

---

### Post by z-vet on 2006-08-30
> **rekahsoft said:**
> what is the hex color for transparent?
Yep, i want to know it too.

---

### Post by rekahsoft on 2006-08-30
crap..supposably there is none...i think this is a bug in ubuntu...it may need to be reported (even tho it is sooo small).

---

