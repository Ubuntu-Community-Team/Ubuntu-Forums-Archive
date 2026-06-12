---
title: "Does anyone know why this happens?"
date: 2010-06-05
forum: General Help
---

### Post by Colo2 on 2010-06-05
I installed kiba-dock from the repos. However, when I tried opening kiba-settings by right clicking on the dock, it didn't work. So I decided to run it in command line to get a text response. This is what I got:

> tom@tom-laptop:/$ kiba-dock

(kiba-dock:11706): GLib-GObject-WARNING **: cannot register existing type `GFileMonitor'

(kiba-dock:11706): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(kiba-dock:11706): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(kiba-dock:11706): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed


Does anyone have any idea why this is? 
Thanks.

---

