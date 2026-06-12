---
title: "Problems with Compiz/Metacity"
date: 2012-02-29
forum: General Help
---

### Post by F1lthym0nk3y on 2012-02-29
Hello fellow Linux users!

First of all I should tell you that I am using Ultimate edition 3.0 which is based on debian and used to be based on ubuntu, but it is essentially a bulked up ubuntu.

I am having some problems with compiz/metacity

I'm trying to configure 6 desktops with rotate cube and desktop cube.. 

I have used these commands to try and replace the old/default settings

compiz --replace
metacity --replace

But they don't use the new settings created within the compiz config manager.. Do I need to uninstall compiz or am I missing something here?

Regards.

---

### Post by F1lthym0nk3y on 2012-02-29
Heres the results from the compiz --replace command

```

$ compiz --replace
Backend     : gconf
Integration : true
Profile     : Wasps
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing resize options...done
Initializing trailfocus options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing kdecompat options...done
Initializing imgjpeg options...done
Initializing titleinfo options...done
Initializing commands options...done
Initializing water options...done
Initializing opacify options...done
Initializing colorfilter options...done
Initializing move options...done
Initializing wallpaper options...done
Initializing wobbly options...done
compiz (core) - Error: Plugin 'text' not loaded.

compiz (shift) - Warn: No compatible text plugin loaded
Initializing shift options...done
Initializing cube options...done
Initializing rotate options...done
Initializing td options...done
Setting Update "border_color"
Setting Update "fill_color"
Setting Update "outline_color"
Setting Update "fill_color"
Setting Update "run_command_terminal_key"
Setting Update "initiate_key"
Setting Update "next_key"
Setting Update "top_color"
Setting Update "bottom_color"
Setting Update "skydome_image"
Setting Update "skydome_gradient_start_color"
Setting Update "skydome_gradient_end_color"
Setting Update "active_opacity"
Setting Update "inactive_opacity"
Setting Update "active_plugins"
compiz (core) - Error: Plugin 'text' not loaded.

compiz (shift) - Warn: No compatible text plugin loaded

```

and the metacity --replace command

```

$ metacity --replace
Window manager warning: Log level 16: Theme directory  of theme Azenis Icons has no size field

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4a0008a (Ubuntu For)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

---

### Post by F1lthym0nk3y on 2012-03-02
:P Bump!

---

### Post by F1lthym0nk3y on 2012-03-02
I'm sorry I do not speak Polish!

---

### Post by F1lthym0nk3y on 2012-03-05
bump

---

### Post by HiImTye on 2012-03-05
set your compiz options and then export your settings, this should be done in [CCSM]("apt://compizconfig-settings-manager") on the left hand side, I believe in 'preferences' or something like that (I use Gnome-Shell so Im not sure of the specifics)

then just import the settings in the other profiles in the same spot

---

