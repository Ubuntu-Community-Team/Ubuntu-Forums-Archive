---
title: "Fully custom looks for Gnome"
date: 2011-03-31
forum: General Help
---

### Post by Inygknok on 2011-03-31
I've been able to change quite a few things in my short time with Ubuntu Maverick, from the Grub menu font and wallpaper to a few other things.

I've been researching on how to fully decorate the window borders and toolbars but I can't seem to get a clear as day answer.  The threads I've found that have plenty of information are quite old (usually 2006), and others lead to things I already had tested with, such as Gnome Color Chooser.  GCC was very nice, but it didn't really do everything I wanted.  For one, I could only change the colors of the Main Menu, but not other menus such as the menus within Firefox (those are still grey with white letters and an orange highlight when hovering).  It also wouldn't change the colors for the factory clock in the taskbar without messing up a bunch of other things.  The list goes on.

What's even more confusing and the reason why I haven't begun is the following.  Some people mention GTK+2, others Metacity, and others COmpiz and others Emerald.  I know what COmpiz and Emerald are, but I don't understand how they're related (or unrelated) to the other 2 terms.  Some threads mention how Emerald offers better functions than the rest, others just talk about editing Metacity themes.

In short, I'm completely lost in the terminology.  I do understand that the editing to get the exact look I want has to be done by hand, and I'm willing to do that.  It's a bit pointless though if I'm stuck with the terminology I've mentioned.  I want to know which themes I can search and be able to edit them to the looks I want.

---

### Post by Krytarik on 2011-03-31
Hi Inygknok,

I must say, that your desktop even after just some days looks already pretty nice!
However, the first glance isn't worth much if it doesn't get applied to all apps, right?!

So, I'll try to clear up the terminology a bit first:

- Metacity: is both
1.) a window manager, it handles the windows
2.) a window decorator, it applies a theme to the borders/titlebar
It can only run its built-in window-decorator.
Because of the dual application of the name, it can be confusing at times.

- Compiz: is a window manager, it handles the windows, but it also handles which window decorator is running, it can run both Metacity (decorator) and Emerald; I guess, the app "gtk-window-decorator" included by Compiz, does in fact just pull the window decorator themes built for Metacity and compute them, while not touching Metacity itself at all

- GTK: is a language used to build the contents of the windows, and a theme can get applied to those; it is in fact no app, whereas all the others are apps

- Emerald: is a window decorator, it applies a theme to the borders/titlebar, it can only run in combination with Compiz

Greetings.

---

### Post by Inygknok on 2011-03-31
> **Krytarik said:**
> Hi Inygknok,

I must say, that your desktop even after just some days looks already pretty nice!
However, the first glance isn't worth much if it doesn't get applied to all apps, right?!

So, I'll try to clear up the terminology a bit first:

- Metacity: is both
1.) a window manager, it handles the windows
2.) a window decorator, it applies a theme to the borders/titlebar
It can only run its built-in window-decorator.
Because of the dual application of the name, it can be confusing at times.

- Compiz: is a window manager, it handles the windows, but it also handles which window decorator is running, it can run both Metacity (decorator) and Emerald; I guess, the app "gtk-window-decorator" included by Compiz, does in fact just pull the window decorator themes built for Metacity and compute them, while not touching Metacity itself at all

- GTK: is a language used to build the contents of the windows, and a theme can get applied to those; it is in fact no app, whereas all the others are apps

- Emerald: is a window decorator, it applies a theme to the borders/titlebar, it can only run in combination with Compiz

Greetings.

It's been mostly thanks to you :D

And thanks for the clarification!  I managed to get the Compiz Fusion Icon to set Emerald as the default themer (or it should be at least).

I have one doubt though.  I started playing around with Emerald and trying to sort of create my own theme. The other themes I had, non .emerald ones, I could install just by right-clicking in my desktop, going to Themes, and dragging them in there.  What's the equivalent for Emerald?

---

### Post by Krytarik on 2011-03-31
> **Inygknok said:**
> 
I have one doubt though.  I started playing around with Emerald and trying to sort of create my own theme. The other themes I had, non .emerald ones, I could install just by right-clicking in my desktop, going to Themes, and dragging them in there.  What's the equivalent for Emerald?
To install themes for Emerald, open "System -> Preferences -> Emerald Theme Manager", click at "Import" at the right upper, then just browse to the downloaded file and open it.

The theme directories get eventually created in "~/.emerald", the "theme" subdirectory contains the currently active theme, and the "theme**s**" subdirectory contains all saved themes.

---

### Post by Inygknok on 2011-03-31
Okay, gotcha!  I'm going to keep wasting my night on this  :p

Thanks for the save again :).  I'll mark this thread as solved once I finish setting up the windows and such in a few hours (just in case I break something).

---

### Post by Inygknok on 2011-03-31
Spent all this time getting the top window borders and such adjusted to where I like it (for one theme variation at least).

Still, I couldn't get any special of the special effects for the taskbar.  I'm also still stuck with the grey menus (like when right-clicking) with orange highlights.

How do I go about edting that?  I know some themes include glassy looks for the taskbar and modified right-click menus.

---

### Post by Krytarik on 2011-03-31
As for fixing the panels regarding custom backgrounds, see my earlier post of today:
[http://ubuntuforums.org/showthread.php?p=10622129#post10622129](http://ubuntuforums.org/showthread.php?p=10622129#post10622129)

What exactly do you mean by "special features" of the taskbar?

As for the stubborn menus, it seems like you really need to manually edit the theme's main config file, it is called "gtkrc" and is located in the "gtk-2.0" subdirectory of the theme.

What theme are you actually trying to modify, it looks like it's basically Maverick's Ambiance?

---

### Post by Inygknok on 2011-04-01
The special taskbar features I mentioned were just to give the taskbar at the bottom a "chrome" or at least glassy look.

I think I ran into a post earlier in the night talking about how to edit that very same file to change the colors in the menus I mentioned.

No theme.  I just started fooling around with all the Emerald settings until I got something I liked.

I'll start giving your post a thorough read in a bit.  I was only able to skim over it earlier.

---

### Post by Inygknok on 2011-04-01
Read the other post you mentioned and tried out the things you mentioned.

However, I kept searching for more information to further understand everything and ran into this:
[http://en.wikibooks.org/wiki/GTK%2B_By_Example/Theming](http://en.wikibooks.org/wiki/GTK%2B_By_Example/Theming)

I copied all the files from the Clearlooks theme folder into a separate one to mess around.  Is there another, maybe more detailed guide that explains a bit further what everything else means?

---

### Post by Krytarik on 2011-04-01
> **Inygknok said:**
> Is there another, maybe more detailed guide that explains a bit further what everything else means?
Unfortunately, theming seems to be an area, that is not very well documented, I also didn't find a comprehensive, user friendly guide, when I searched once. All I know about themes, I've learned through studying the code while modifying it, and adhoc web searches for specific code details, most of those searches ended up here:
[http://library.gnome.org/devel/gtk/stable/](http://library.gnome.org/devel/gtk/stable/)
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

---

