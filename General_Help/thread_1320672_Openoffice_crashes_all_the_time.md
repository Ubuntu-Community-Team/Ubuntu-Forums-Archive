---
title: "Openoffice crashes all the time"
date: 2009-11-09
forum: General Help
---

### Post by Radissthor on 2009-11-09
Hello everyone.

I don't know if this is the correct place to post this. If not, please let me know. 

I've been having a lot of problems with Openoffice. EVERYTIME (and I mean every time) I try to save a file in a different format that's not .odt all openoffice applications crash. I'm sometimes able to recover them, but this is driving me mad! I need to saver documents in.doc format to get around work. I uninstalled and reinstalled openoffice, but the problem persists.
I read that it was better to download openoffice from SUN and not from the synapctic package manager, but I didn0t get how to download it from SUN. All I get when I do that is a bunch of folder with no file that can isntall the program. 

Please, I would really appreciate any help you may provide. This is bringing me too many complications :( 

By the way, I'm using Ubuntu 9.10 Karmic Koala

---

### Post by scouser73 on 2009-11-09
I'd suggest that you delete your OpenOffice profile, go to your home folder and press **CTRL & H** and delete the folder **.openoffice.org**

Now restart OpenOffice and try to save a file, and see what the outcome is.

---

### Post by Giblet5 on 2009-11-09
Try creating a test user named "ed".

Log in as that user, open a document or create one. Save it in Word-XP format. Did it work?

If so, something in your regular account's settings is causing the problem. But at least you can edit documents as user ed, right?

Easy way to move your non-working config aside and start over with defaults:

```
mkdir dotbackup
mv .config .gconf* .kde dotbackup
sudo /etc/init.d/gdm restart
```

---

### Post by Radissthor on 2009-11-09
I did what you said. Docs keep crashing when saved in .doc format... :(

---

### Post by Giblet5 on 2009-11-09
Try using the 'ed' user to open an existing OO doc.

Now, open a new blank document. Select everything from the first doc, paste it into the second (empty) doc, then save that as Word format.

Did that work?

---

### Post by Radissthor on 2009-11-09
I created a new used called ed
I logged in as ed
I opened an OO file, saved it as doc and it all went well

I then logged with my regulatr login name
Y opened the terminal and typed:

mkdir dotbackup
mv .config .gconf* .kde dotbackup
sudo /etc/init.d/gdm restart

I opened a new OO file. Tried saving it as .doc and it crashed again...

I opened a new file, pasted the content of the old file and tried saving it as .doc
it crashed again....

This is driving my crazzzy!!!!

By the way, I tried deleting the .opeoffice folder in Home. No luck either...

---

### Post by Giblet5 on 2009-11-09
Try executing this, then trying that last test again: ```
mv .openoff* dotbackup
```

---

### Post by Radissthor on 2009-11-09
I get an error:

hernan@Inspiron1525:~$ mv .openoff* dotbackup
mv: cannot stat `.openoff*': No such file or directory
hernan@Inspiron1525:~$ 


:(.....

---

### Post by Giblet5 on 2009-11-09
I guess it's something else in your environment...

After a crash, look at ~/.xsession-errors and see if OO is telling you what's wrong.

---

### Post by Radissthor on 2009-11-09
And where might I find that folder or file?

---

### Post by Giblet5 on 2009-11-09
~/.xsession-errors

aka $HOME/.xsession-errors

```
less ~/.xsession-errors
```
or
```
gedit ~/.xsession-errors
```

---

### Post by Radissthor on 2009-11-09
Ok this is big... SOrry if I'm a brute to post it:

-------------------------------------------------


/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-ugYjeK/socket
SSH_AUTH_SOCK=/tmp/keyring-ugYjeK/socket.ssh
GNOME_KEYRING_PID=2934

(gnome-settings-daemon:2931): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:2931): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 

(nautilus:3028): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** Message: Reading of RFKILL events failed
** Message: killswitches state 3

(polkit-gnome-authentication-agent-1:3050): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3050): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: killswitches state 3
** (gnome-panel:3027): DEBUG: Adding applet 0.
** (gnome-panel:3027): DEBUG: Initialized Panel Applet Signaler.

** (nautilus:3028): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3028): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3028): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
** (gnome-panel:3027): DEBUG: Adding applet 1.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
** (gnome-panel:3027): DEBUG: Adding applet 2.
** (gnome-panel:3027): DEBUG: Adding applet 3.
** (gnome-panel:3027): DEBUG: Adding applet 4.
** (gnome-panel:3027): DEBUG: Adding applet 5.
** (gnome-panel:3027): DEBUG: Adding applet 6.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** (gnome-panel:3027): DEBUG: Adding applet 7.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (gnome-panel:3027): DEBUG: Adding applet 8.
** (gnome-panel:3027): DEBUG: Adding applet 9.
I/O warning : failed to load external entity "/home/hernan/.compiz/session/1011702265af84015b125779090847665700000028490023"
** (gnome-panel:3027): DEBUG: Adding applet 10.
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
** (nm-applet:3034): DEBUG: foo_client_state_changed_cb

(nautilus:3110): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (nm-applet:3034): DEBUG: foo_client_state_changed_cb

(gnome-appearance-properties:3159): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
evolution-alarm-notify-Message: Setting timeout for 20259 1257811200 1257790941
evolution-alarm-notify-Message:  Mon Nov  9 21:00:00 2009

evolution-alarm-notify-Message:  Mon Nov  9 15:22:21 2009


(gnome-appearance-properties:3195): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(nautilus:3198): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:3222): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(nautilus:3295): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:3027): DEBUG: Adding applet 11.
** (gnome-panel:3027): DEBUG: Removing applet 11.
** (gnome-panel:3027): DEBUG: Adding applet 11.
** (gnome-panel:3027): DEBUG: Removing applet 11.
** (gnome-panel:3027): DEBUG: Adding applet 11.

(yelp:3312): Yelp-WARNING **: Failed to load config file: No such file or directory


** (yelp:3312): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (yelp:3312): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(nautilus:3317): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
GConf Error: Bad key or directory name: "/desktop/gnome/url-handlers/": Key/directory may not end with a slash '/'

(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(nautilus:3595): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3275): Gdk-WARNING **: XID collision, trouble ahead

(nautilus:3719): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(nautilus:3842): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gtk-window-decorator:3071): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:3027): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8

---

### Post by Giblet5 on 2009-11-09
Try starting OO via the command line, capturing its output.

Try to reproduce the crash, then post the output (after you hit the '#' gadget at the top of the comment editor so it goes inside a CODE block.)

```
oowriter > oo.log 2>&1
```

---

### Post by Radissthor on 2009-11-09
> **Giblet5 said:**
> Try starting OO via the command line, capturing its output.

Try to reproduce the crash, then post the output (after you hit the '#' gadget at the top of the comment editor so it goes inside a CODE block.)

```
oowriter > oo.log 2>&1
```

How do you mean? I typed oowriter on the terminal, but it just opens Openoffice, no output generated. I copied the code you wrote, but again, only opens openoffice, but no output.

Am I doing something wrong?

---

### Post by Giblet5 on 2009-11-09
> **Radissthor said:**
> How do you mean? I typed oowriter on the terminal, but it just opens Openoffice, no output generated. I copied the code you wrote, but again, only opens openoffice, but no output.

Am I doing something wrong?

The output will go to oo.log in your home directory.

Once OO crashes, open that file with gedit or whatever you like and post the contents.

If the file is empty, OO generated no errors (seems unlikely).

---

### Post by Radissthor on 2009-11-09
Ok I pased the code code you gave me and it opened OO. I Copied a file I want to save in .doc and tried to save it in that format. The document crashed and I went to the file in the Homefolder you mentioned, but the file is empty...

---

### Post by Hagar Delest on 2009-11-09
See [Reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Radissthor on 2009-11-10
Ok, sorry it took me so long to reply, but the process was quite complicated for a Newbie like me.

The first suggestion of erasing the profile didn't work, so I went for the second option:

I wrote openoffice on the search field of the Synaptic Package Manager and marked for "Complete Removal" all the installed openoffice packages.

I downloaded OOo from the ofcial webpage. I selected the Linux DEB version since I'm using Ubuntu Karmic Koala. 

Then I installed the download from the terminal as indicated by the tutorial referred to by **Hagar de l'Est**. There were some strange outputs in the terminal, of which I'll post those I thought were more fishy:

```
Setting up openoffice.org3-draw (3.1.1-19) ...
Setting up openoffice.org3-en-us (3.1.1-19) ...
Setting up openoffice.org3-impress (3.1.1-19) ...
Setting up openoffice.org3-math (3.1.1-19) ...
Setting up openoffice.org3-writer (3.1.1-19) ...
Setting up ooobasis3.1-binfilter (3.1.1-19) ...
Errors were encountered while processing:
 desktop-integration
 .deb
hernan@Inspiron1525:~/OOO310_m19_native_packed-1_en-US.9420/DEBS$ 





hernan@Inspiron1525:~/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration$ sudo dpkg -i * .deb
Selecting previously deselected package openoffice.org-debian-menus.
(Reading database ... 168900 files and directories currently installed.)
Unpacking openoffice.org-debian-menus (from openoffice.org3.1-debian-menus_3.1-9420_all.deb) ...
dpkg: error processing .deb (--install):
 cannot access archive: No such file or directory
Setting up openoffice.org-debian-menus (3.1-9420) ...
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.

Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'


hernan@Inspiron1525:~/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration$     sudo dpkg -i *.deb
(Reading database ... 169225 files and directories currently installed.)
Preparing to replace openoffice.org-debian-menus 3.1-9420 (using openoffice.org3.1-debian-menus_3.1-9420_all.deb) ...
Unpacking replacement openoffice.org-debian-menus ...
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
Setting up openoffice.org-debian-menus (3.1-9420) ...
/usr/bin/gtk-update-icon-cache
/usr/bin/gtk-update-icon-cache

Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Errors were encountered while processing:
 .deb
hernan@Inspiron1525:~/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration$ 

```

After that, OOo was again installed on my computer. I opened a .odt document and..........it crashed!! But then I did the whole welcome process of OOo and then I opened the .odt file I have wanted to convert to .doc. It Worked fine!! I saved a couple of .odt files to .doc without any problems either, si I guess the fix worked! Many thanks!!:D

Now, to round up, after removing the packages, the mozilla icon that was in the toolbar (right next to the help sign) disappeared, to be replaced by a circle with a crossed line. When I click it, it says: 

Could not launch application
Failed to execute child process "firefox" (No such file or directory)

Now, obviously, Firefox is working (I'm writing from it). Also, I had some language packages installed in OOo (spanish grammar corrector) and I would like to reinstall those, but I'm afraid of running the update manager and get the wrong OOo configuration again.

What should I do??


*Edit*: Ok, so Firefox was uninstalled. I rebooted to see if that would fix it but no. So I went to the Terminal and typed
```
sudo apt-get install mozilla
```
And the output was:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla: Depends: seamonkey but it is not going to be installed
E: Broken packages

```

I guessed I needed Seamonkey, so I run
```
sudo apt-get install seamonkey
```

And it installed OK. I opened the browser and it said I was running an old version, so I clicked to download the upgrade from the webpage. It is a .tar file but I don't know how to install it.

Anyway, I would like to have Mozilla back. But when I try to install it through terminal, it gives me the same error. Idon't know if I'm doing something wrong, but it is very likely. 

If I run mozilla on safe mode from terminal, it opens and, to my surprise, it still has my configuration! with all my bookmarks and all that...

I would appreciate some help on this please... :frown: :confused: :frown:

---

### Post by Radissthor on 2009-11-10
Please help. Now, I don't know why, OOo doesn't open ANY file. be it odt or whatever. As soon as I click on a file, or try opening OOo, it crashes. I can't even recover files because the recoveries also crash.

Things are worse than when I first started to solve the problem... And I'm beginning to despise OOo... It's given so much problems...:mad:

BTW: Mozilla Firefox and Update manager continue not working... My Ubuntu is really ****** up and I don't know why!! :'(

---

### Post by Hagar Delest on 2009-11-10
That's really strange indeed. There is a problem since there is no link between Firefox and OOo.

Try to remove OOo (you can still use Synaptic for that) and be sure there is no more OOo packages (especially those with 'ubuntu' in the version name).

Then try to repair the broken packages, reinstall Firefox for example. I'm not sure moving the .config and .gconf files was a good idea. There is no link with OOo. Can you try to move them back?

---

### Post by Radissthor on 2009-11-10
> **Hagar de l'Est said:**
> That's really strange indeed. There is a problem since there is no link between Firefox and OOo.

Try to remove OOo (you can still use Synaptic for that) and be sure there is no more OOo packages (especially those with 'ubuntu' in the version name).

Then try to repair the broken packages, reinstall Firefox for example. I'm not sure moving the .config and .gconf files was a good idea. There is no link with OOo. Can you try to move them back?

I went to Synaptic Package manager and I clicked a package was not installed. It automatically uninstalled some and now OOo is working again (for the moment, at least). 

I still have the problem with Mozilla and Update Manager. I'm currently using Mozilla, but I can only open it through terminal in -safe-mode and I can run updates and upgrades from terminal as well... 

How would you recommend to uninstall and reinstall firefox? I was able to install seamonkey but with Firefox I had troubles. I have a very customized firefox and I would not like to loose that (but I will if there's no other choice). 
Thanks for the help...:)

EDIT: When I try running firefox from terminal, it says:

```
hernan@Inspiron1525:~$ firefox

(process:2198): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(firefox:2198): Gdk-WARNING **: locale not supported by C library
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
Aborted
hernan@Inspiron1525:~$
```


EDIT 2:

Since I opened Firefox -safe-mode from terminal, I've been getting the following output:
```

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead

(firefox:3964): Gdk-WARNING **: XID collision, trouble ahead
```

---

### Post by Hagar Delest on 2009-11-10
Are you running Karmic? Google with the "XID collision, trouble ahead" error message and you'll find several bugs in the launchpad. I think you've come across a bug, but not related to the OOo upgrade.

---

### Post by Radissthor on 2009-11-10
Yes, I'm on Karmic and let me tell you it's been hell... 

Yes, I googled it and I saw lots of bugs reports, but I'm really a newbie at Linux (and computers in general, though I try hard =P) and so don't know how I can use that information to solve my problem. I tried reading some but got lost along the way (more like the beginning actually...)

What do you think i should do?:lol:

---

### Post by Hagar Delest on 2009-11-11
Well, here is how I do on my laptop: I've several partitions in order to run 2 flavors in dual boot.
- 1 partition for the stable version that I know is working fine (currently Hardy), 7GB
- 1 partition for another flavor, I use this one to install a new one and test it. If I like it and if there is no critical bug for me, I keep it, make it the default boot partition and will use the first one to test the next release. 7GB
- 1 partition for my documents, mounted as /home/my_username/Documents to keep all my personal files in a dedicated places that won't be overwritten when installing an upgrade, 20GB (up to you depending on your computer use).
- 1 partition for the main profiles (OOo, Thunderbird and Firefox) and replace the default one created at each install by a link to these folders so that I keep all my settings at each upgrade, 5 GB.
- 1 partition for the /opt directory avoiding reinstalling latest Java, OOo, Firefox, Thunderbird, ..., 10GB.
- 1 partition as backup, 30GB.
- 1 partition for the swap of course, depending on your RAM.

It can seem rather complicated but this way you're sure to always have a stable version at hand, you can test the new release without messing all the system and keeping the personal settings.

By the way, better install from scratch, that means with a CD instead of the online upgrade: the latter method has been proved less efficient (personal experience and many topics here also) because some old items remain and can cause some troubles. This is why different partitions are important. The only trick is to write somewhere the names of the partitions and what's inside so that you don't overwrite the wrong one when you install a new release.

To conclude, what I would do is:
- backup all important files (documents and even some profiles like FF or TB, especially if you have a lot of registered logins)
- install from scratch the last working Ubuntu version, partitioning the HD
- then install Karmic on its partition (installer will create the dual boot, don't worry)
- use the last working release and monitor the resolution of the bug for XID
- once the bug is fixed, try Karmic, update it by installing the latest changes and change the default boot option if needed to start automatically the release you want.

The key point IMHO is the partitioning system that will insure the safety of your data by separating each area.

---

### Post by Radissthor on 2009-11-11
Wow it's a shame the bug is so complicated to fix. 

I only have 80GB of HD so I'm avoiding partitions. I hardly have enough space using one. 

I think I'll just back up my files and do a fresh install of Ubuntu Jaunty. Koala seemed so cool, but man was it full of problems! Using my laptop on karmic was really anoying. 

Is this the same with alkl new releases? I'm very new at Ubuntu and my first user-experience was with Jaunty just this year, so Karmic was my first upgrade experience... Should I always wait for new versions to stabilize before upgrading?

Thanks for the help. I appreciate it. :)

---

### Post by strange_cathect on 2009-11-11
Hello, all.

I am having similar issues. If I try to save a file in .odt all is well. However, if I save to .doc Writer frequently crashes.

Also, when I am able to save a file as a .doc, the notes I have made within the document do not save (they are gone when the file is re-opened).

I followed your advice to rename my profile and force the creation of a new one. This did not resolve either error.

---

### Post by Hagar Delest on 2009-11-13
> **Radissthor said:**
> Wow it's a shame the bug is so complicated to fix.
Well, my proposal is a generic tip, it's not specific to this bug. NB: after a hardware problem, I had to move to another laptop, I installed Katmic (xubuntu) and it's running fine. But I use the Mozilla version (3.6 beta 2). No issue at all.

> **Radissthor said:**
> I only have 80GB of HD so I'm avoiding partitions. I hardly have enough space using one.
My HD is also 80GB. I were you, I would not make big partitions. Because if there is a problem, you lose a lot of data at once! If you make several partitions, with smaller size, in case of damage you lose only the partition that is wrecked with less impact on the rest of your data.

@ strange_cathect: try the Sun version perhaps and make sure that this is not a RTF file (they can be labelled .doc also.

---

### Post by strange_cathect on 2009-11-14
Hagar,

I purged every open office package, then installed from the Sun debs. Same problem. Crashes when dealing with .doc files. This seems to be a Karmic issue...

---

### Post by Hagar Delest on 2009-11-14
Can you upload a sample file somewhere (mediafire for example) where you can reproduce the crash or the notes disappearing?

---

### Post by strange_cathect on 2009-11-15
Hagar,

One of my student's file may be found here:

[http://www.mediafire.com/?tbwywzyz2zx](http://www.mediafire.com/?tbwywzyz2zx) 

I am able to create one note on this document and save it as normal. Adding a second note, however, will cause a crash every time I attempt to save it. 

This does not happen with .odt.

---

### Post by Hagar Delest on 2009-11-15
Works fine for me with OOo 3.1.1 (Sun version) on my xubuntu Karmic box, see: [http://www.mediafire.com/?ttm2ym5h1xo](http://www.mediafire.com/?ttm2ym5h1xo)

---

### Post by peterroots on 2009-11-18
Just to add to this.
I can download the document [http://www.mediafire.com/?tbwywzyz2zx](http://www.mediafire.com/?tbwywzyz2zx) and open it.
I can save it under a new name, no prob.  I can edit it and save it (still as .doc) no prob.
I can add a comment to it but if I save it OOO crashes - Kubuntu karmic with openoffice up to date as of yesterday

I can add comments to this doc and save it (and do other edits) if I save it as .odt first.

Out of interest another good way to crash OOO is to open the extension manager from tools and click 'update' - I was googling for this problem when I found this post and thought I would see if I could add notes to a .doc just for fun.  (update to karmic from Jaunty used alternative CD method)

Another interesting thing the doc, downloaded here, has nothing in the status bar apart from the page zoom control but if I press insert then OVER appears and I can cycle through the usual options. A new document has the language displayed the 'not modified' icon and the icons for single double and facing pages as well as the zoom tool. Editing the new document changes the not modified icon to not saved but no icon appears in the test doc from here. A document of mine, started pre upgrade and edited since, has the pages and style in the status bar as well as the above mentioned and not mod/not saved works as expected.
Does all this suggest there is something rather fundamental wrong rather than just a weeny (but incredibly annoying if you need it) bug in the notes in .doc format issue?

I also tried selecting 'use openoffice dialog boxes' (the tools dialog has the spacing all messed up as well) to see if that made a difference - it does not

---

### Post by peterroots on 2009-11-18
I found a post on the Kubuntu forum recommending removal of the kde integration package - that fixes the mucked up status bar and extension update crash but it has no effect on the notes in a .doc
That has made me happy but, sorry, not much help to you. :(

---

### Post by TWO on 2009-11-30
> **peterroots said:**
> I found a post on the Kubuntu forum recommending removal of the kde integration package - that fixes the mucked up status bar and extension update crash but it has no effect on the notes in a .doc
That has made me happy but, sorry, not much help to you. :(

Removing the KDE integration package for me still doesn't enable me to install the languagetool extension, the only difference is that instead of crashing completely it just displays a very long cryptic error and then allows me to continue using the program. So the kde package is probably only part of the problem...

---

### Post by TWO on 2009-11-30
OK! My problem relating to Openoffice.org crashing when I tried to install an extension has been resolved!

On deeper reading of the instructions from the following page concerning the extension I wanted: [http://www.languagetool.org/](http://www.languagetool.org/) it appears that you need the ```
openoffice.org-java-common
``` package installed in order to be able to install extensions. I wonder if this is related to the other problems people have faced on this page...

TWO

---

### Post by peterroots on 2009-12-01
It is possible the missing java common is a problem for some - was not the case for me as I use office base and java is essential for that as well so I had that installed from the begining

---

### Post by BruceGF on 2010-03-28
I was editing a .doc file using track changes. Open Office crashed when I tried to save it as .doc but I was able to save as .odt or .docx. Might be a useful workaround for some.

---

