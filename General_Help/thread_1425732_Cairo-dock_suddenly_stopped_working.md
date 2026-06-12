---
title: "Cairo-dock suddenly stopped working"
date: 2010-03-09
forum: General Help
---

### Post by JTwigg on 2010-03-09
Hello everyone. I am a proud user of ubuntu and basically this is my desktop:

I have got rid of the bottom gnome taskbar and replaced it with cairo-dock and the top toolbar is only showing one pixel with a delay scroll down so when i hover by it it doesnt keep popping down unless i leave the mouse there. anyway thats besides the point.

i use cairo-dock and have done for over 4 months. then all of a sudden it stopped working. I don't have a clue why, perhaps you have encountered this problem and know of a solution.

im using 9.04 jaunty and latest cairo-dock.

when i type cairo-dock -c into terminal i get:

cairo-dock: /usr/lib/libxml2.so.2: no version information available (required by cairo-dock)

 ============================================================================ 
    Cairo-Dock version: 2.1.4-0alpha1
    Compiled date:  Mar  4 2010 20:19:19
    Running with OpenGL: 0
 ============================================================================

warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  while opening module '/usr/lib/cairo-dock/libcd-weblets.so' : (libwebkit-1.0.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  while opening module '/usr/lib/cairo-dock/libcd-keyboard-indicator.so' : (libxklavier.so.15: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-config.c:cairo_dock_get_integer_key_value:142)  
  Key file does not have key 'use class indic'
warning :  (cairo-dock-opengl.c:cairo_dock_create_icon_fbo:312)  
  No FBO support, applets can't draw themselves inside the dock.
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:185)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:185)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/donaldduck/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
cairo-dock: symbol lookup error: cairo-dock: undefined symbol: gdk_x11_window_get_drawable_impl



any help would be greatly appreciated as pressing ALT-TAB is getting on my nerves a bit ... :P



PS i use the non OpenGL option.

---

### Post by fabounet on 2010-03-10
you're missing several dependencies.
you could consider using the stable release (2.1.3-6)

---

### Post by shockandawe on 2010-03-10
Try Docky 2.1. Although it has less options, it is MUCH better than cairo dock. It's faster and also looks stunning.

Once I installed it, I never looked back.

---

### Post by El Zoido on 2010-03-10
Can it be that a recent update broke your cairo-dock?

Docky is indeed a nice alternative if you are just looking for a basic dock. 
I've been using it in its Gnome-Do form for quite some time now and recently updated to 2.1, wich I really like so far.
Cairo-dock offers far more possibilities for personalization though.

---

### Post by JTwigg on 2010-03-10
wow thanks for the quick response. it might have been after an update, it sometimes updates once a week tho. I'm also running cairo-dock on my desktop pc but that one is fine. I will try docky.
Many thanks.
:D

---

### Post by fabounet on 2010-03-11
If you're on the weekly version it might indeed break sometimes (remember, it's the development version).
You may want to use the stable version then (2.1.3).

In term of speed, nothing can compete with OpenGl ;-)

---

