---
title: "xbmc and nvidia driver issue"
date: 2010-03-24
forum: General Help
---

### Post by dinozzo on 2010-03-24
Hi, I have installed ubuntu using the mini iso, nothing extra was installed until I got to login. I then installed ssh, proftpd, vim, zip, and build dependancies used to compile xbmc. I installed the nvidia drivers using this method:

add-apt-repository ppa:nvidia-vdpau/ppa

apt-get update

apt-get install nvidia-glx-195 nvidia-195-modaliases

I then proceeded to compile xbmc which went without a hitch.
Now for the problem! It says I can start xbmc by typing xbmc at the prompt. When I do it returns this:

Error: unable to open display
XBMC needs hardware accelerated OpenGL rendering.
Install an appropriate graphics driver.

Why is it saying this when I installed the nvidia drivers earlier? And more importantly how can I solve this issue?

I would be greatful for an assistance.
TIA

---

### Post by jsriz on 2010-03-24
since you have installed from a mini.iso you wont have xserver and gdm 
install them and try to open display.......
I don't think you have any plans to install the "ubuntu-desktop" package which would take care of everything but will have everything of a normal install...

---

### Post by dinozzo on 2010-03-24
I have installed the packages you suggested and am now able to run xbmc but it returns a page of error code:

root@ubuntu:/# xbmc
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Error: unable to open display
/usr/share/xbmc/FEH.py:66: Warning: invalid (NULL) pointer instance
  window = gtk.Window(gtk.WINDOW_TOPLEVEL)
/usr/share/xbmc/FEH.py:66: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  window = gtk.Window(gtk.WINDOW_TOPLEVEL)
/usr/share/xbmc/FEH.py:80: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  button = gtk.Button("Quit")
/usr/share/xbmc/FEH.py:80: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  button = gtk.Button("Quit")
/usr/share/xbmc/FEH.py:85: GtkWarning: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
  window.show_all ()
/usr/share/xbmc/FEH.py:85: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_layout_new: assertion `context != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_layout_set_text: assertion `layout != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_layout_set_alignment: assertion `layout != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_layout_set_width: assertion `layout != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_layout_get_extents: assertion `layout != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: PangoWarning: pango_layout_set_attributes: assertion `layout != NULL' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: GtkWarning: gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: GtkWarning: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: GtkWarning: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed
  window.show_all ()
/usr/share/xbmc/FEH.py:85: GtkWarning: gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed
  window.show_all ()
/usr/bin/xbmc: line 70: 20883 Segmentation fault      python /usr/share/xbmc/FEH.py "$@"

Do I need to configure some nvidia settings for my display or something?

---

### Post by jsriz on 2010-03-24
> **dinozzo said:**
> I have installed the packages you suggested and am now able to run xbmc but it returns a page of error code:

if you are able to run xmbc then you need not worry about those warnings those appear when you run some gui app from terminal 
here is something from my system when i run and close nautilus 
```

Gtk-Message: Failed to load module "rgba": librgba.so: cannot open shared object file: No such file or directory
Initializing nautilus-gdu extension

--- Hash table keys for warning below:
--> inode/directory
--> l2053
--> root
Shutting down nautilus-gdu extension

(nautilus:3758): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:3758): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

```

---

### Post by dinozzo on 2010-03-24
When I say im able to run xbmc I mean its not saying it cant find opengl rendering, I still think its not working. I tried rebooting and now ive got some user select screen instead of a terminal login prompt. I logged in and get to some kind of desktop - completely blank with a mouse cursor. I tried typing xbmc from my main pc via ssh and nothing happens on the xbmc machine. I still get the error on the pc:

/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning:  could not open display
  warnings.warn(str(e), _gtk.Warning)
Error: unable to open display

etc.....

Is it pointless and too much hastle me trying to do this from a mini iso and would be better if I installed a propper ubuntu dist?

---

### Post by jsriz on 2010-03-24
it installed gdm and xorg server so it is trying to give you a graphical login
but you dont have the other dependencies like a gnome desktop manager
if you want a minimal install you have to make a list of all these dependecies
you can get your terminal by pressing ctrl+alt+F1
> **dinozzo said:**
> 
I logged in and get to some kind of desktop - completely blank with a  mouse cursor. I tried typing xbmc from my main pc via ssh and nothing  happens on the xbmc machine

as far as i know you cannot open display from the ssh terminal
> **dinozzo said:**
> 
Is it pointless and too much hastle me trying to do this from a mini iso and would be better if I installed a propper ubuntu dist?
yup thats true
Now press Ctrl + alt +F1 and login in the ttyl1 
then install the package "ubuntu-desktop"
that will give you a normal install 
if you want it back to your initial state just purge the installled packages...

---

