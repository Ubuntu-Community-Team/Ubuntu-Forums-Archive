---
title: "lost 1280x1024 resolution, how to edit xorg.conf???"
date: 2006-05-11
forum: General Help
---

### Post by tommcd on 2006-05-11
After dowloading some updates via synaptic I have lost 1280x1024 resolution in: system>preferences>screen resolution. Everything else OK. I tried:
'sudo dpkg-reconfigure-xserver-xorg'  several times without success. After much searching on the forums, I think I need to edit xorg.conf file. Problem is, I can't seem to do it and make it work! when I type:
sudo gedit /etc/X11/xorg.conf
nothing happens, I just get a blinking cursor. When I try:
 sudo nano etc/X11/xorg.conf
I can then edit the file to type in 1280x1024, but when I close the terminal the changes do not stick. If I open the file again the changes I made are not there. What am I doing wrong? How do I edit this file and save the changes to get 1280x1024 back? Any help appreciated thanks! Monitor is Samsung syncmaster 930B.

---

### Post by Piggah on 2006-05-11
Well the command you're entering to open it in gedit should work really, I'm not sure why it's not. 

Are you sure you're saving correctly in nano? Ctrl+x > y > enter?

You could also try opening gedit, in superuser mode of course, and then opening the file through it's menu. Just an idea.

---

### Post by tommcd on 2006-05-11
1) Is that how I save in nano? Hold down control + x. then y, then enter??
2) I just tried sudo gedit etc/X11 xorg.conf again, after a long wait I got:
** (gedit:8203): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(gedit:8203): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(gedit:8203): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_add_child: assertion `BONOBO_IS_MDI (mdi)' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDOW (win)' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: bonobo_window_flash: assertion `win != NULL' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_add_views: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi)' failed
What is this? Is this why its not working? Thanks for the reply.

---

### Post by tommcd on 2006-05-11
Oh, and how do I open gedit in super user mode? Isn't that what I'm doing with sudo?

---

### Post by az on 2006-05-11
Boot into recovery mode (or hit CTRL-ALT-F1, log in and run "init 1" - same thing)

Then run

dpkg-reconfigure -phigh xserver-xorg

and that should restore your config to what it was originaly. 

Run 

init 2
to get back into the desktop.

---

### Post by tommcd on 2006-05-11
1) Thanks Azz, I'll try that.
2) I did manage to edit the file with sudo nano /etcX11/xorg.conf. At the top of the file it said: "If you have edited this file and want it updated run sudo dpkg-reconfigure xserver-xorg to update. I did and I could NOT boot into the GUI. It said xorg was all screwed up. I repeated it and declined autodetect and I'm back in (pheww!!) Should I edit the file back the way it was before trying your suggestion? Will I be able to boot into the GUI? Please reply, and thanks for the help.

---

### Post by tommcd on 2006-05-11
I fixed it!!! Um, it turns out, when I did: 
sudo dpkg-reconfigure xserver-xorg
I FORGOT to select the monitor resolution modes with the spacebar!! Geez, what should have taken 5 minutes to fix has taken me all day!!! (Guess that's the price you pay for an education)!!
I still had to decline all monitor autodetect options to get it to boot. I'm not sure why.
Ubuntu is great IMO. All the clueless screwing around I've done to it, and I STILL haven't broken it!!
Thanks for the help guys!!

---

