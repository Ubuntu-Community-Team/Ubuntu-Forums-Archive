---
title: "Desktop icons missing and 'Places' links not working."
date: 2010-06-19
forum: General Help
---

### Post by Dakan on 2010-06-19
Hi Folks

I have a current problem where my desktop icons are missing and the Places links like Video and Pictures won't load. 'Opening Pictures' etc appears on the taskbar for a few seconds then disappears without opening it.

I have searched other forums and I think this is a problem with either Nautilus or Gnome. When I run Nautilus in Terminal, I get this;
(nautilus:2012): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2012): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2012): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2012): WARNING **: No marshaller for signature of signal 'ShareCreateError'

(nautilus:2012): GLib-GIO-CRITICAL **: g_file_info_set_attribute_string: assertion `attr_value != NULL' failed

(nautilus:2012): GLib-GIO-CRITICAL **: g_file_info_set_attribute_string: assertion `attr_value != NULL' failed

(nautilus:2012): GLib-GIO-CRITICAL **: g_file_info_set_attribute_string: assertion `attr_value != NULL' failed
Segmentation fault

I have tried reinstalling Nautilus (sudo apt-get install nautilus). Didn't work. I also tried to reinstall Gnome. First got an error message saying dependencies were missing. Downloaded Gnome-core, then Gnome again. It seemed to install but still didn't solve the problem. 

I would be very grateful for any assistance.
Kind Regards - Dakan

---

### Post by wojox on 2010-06-19
Try Alt+F2 and type in gconf-editor

Then go to apps > nautilus > desktop and see if your icons are checked.

---

### Post by cariboo on 2010-06-19
Create another user to see if that user has the same problem, if that works you can move all your important files to the new user, and get rid of the old one.

---

### Post by Dakan on 2010-06-20
Hi wjox, 
I looked at that, the icon_visible tickboxes were not ticked so I ticked them and icon_name values are set to <no value>.

Ticking the boxes hasn't made a difference.

cariboo907; When I go to System-Admin-Users and Groups, the Add User button is greyed out.

Any other suggestions? Thanks for responding to me so far.

Dakan

---

### Post by wojox on 2010-06-20
I think cariboo907's idea should work.

Follow this and use the you terminal [https://help.ubuntu.com/community/AddUsersHowto#Command-line](https://help.ubuntu.com/community/AddUsersHowto#Command-line)

---

### Post by NCLI on 2010-06-20
Sounds like your nautilus config has been messed up. Nautilus the file manager for Gnome, but it also handles painting the icons on your desktop.

Like others have suggested, the simplest solution is simply to create a new user.

---

### Post by Dakan on 2010-06-20
I have created a new user and that worked. 
Thanks to everyone who took the time to reply.

One last thing can anyone tell me how to get access privileges to my old user in order to copy everything over to the new one.

Thanks.

---

