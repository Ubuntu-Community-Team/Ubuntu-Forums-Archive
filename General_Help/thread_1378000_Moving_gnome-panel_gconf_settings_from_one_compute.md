---
title: "Moving gnome-panel gconf settings from one computer to another"
date: 2010-01-10
forum: General Help
---

### Post by altonbr on 2010-01-10
I have a bunch of gconf settings that I change by default when I install Ubuntu on someone's machine and thus I've created a script to make it easier after a fresh installation.

Here is a list of changes I make so far:
```
# jump-to-paying
gconftool-2 --type bool --set /apps/rhythmbox/plugins/jump-to-playing/active "true"
# desktop
gconftool-2 --type int --set /desktop/gnome/thumbnail_cache/maximum_age "60" # only allow thumbnails for 60 days
gconftool-2 --type string --set /desktop/gnome/interface/document_font_name "Myriad Pro Condensed 12" # change document font
gconftool-2 --type string --set /desktop/gnome/interface/font_name "Myriad Pro Condensed 12" # change document font
gconftool-2 --type bool --set  /apps/nautilus/desktop/computer_icon_visible "true"
gconftool-2 --type bool --set  /apps/nautilus/desktop/home_icon_visible "true"
gconftool-2 --type bool --set  /apps/nautilus/desktop/trash_icon_visible "true"
# gedit
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/auto_indent/auto_indent "true" # auto-indent on
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/current_line/highlight_current_line "true" # add highlight for current line
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/font/use_default_font "false" # turn off default font settings
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/line_numbers/display_line_numbers "true" # show line numbers
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/save/auto_save "false" # turn off auto saving
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/save/create_backup_copy "false" # turn off backups
gconftool-2 --type int --set /apps/gedit-2/preferences/editor/tabs/tabs_size "4" # turn off backups
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/colors/scheme "oblivion" # change theme to oblivion
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/font/editor_font "Monaco 10" # change font
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode "GTK_WRAP_WORD" # text wrap on
# gnome-screenshot
gconftool-2 --type bool --set  /apps/gnome-screenshot/include_pointer "false" # turn off mouse pointer in screenshots
# nautilus
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible "false" # do not show volumes on desktop
gconftool-2 --type string --set /apps/nautilus/preferences/date_format "iso" # iso date format
gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer "list" # change nautilus to show list view
gconftool-2 --type string --set /apps/nautilus/preferences/desktop_font "Myriad Pro Condensed 12" # desktop font
```

However, I'm looking to remove the top panel and have only the bottom panel like I have set up on my machine. The gconf settings seem to be pretty complex and I'm not sure which keys I should be changing to remove the top panel and include the settings I have currently for the bottom panel (e.g. Menu Bar | Shortcuts | Window List | Notification Area | Clock)

Just hoping someone has knowledge of gnome-panel and gconf. Thanks!

---

### Post by altonbr on 2010-01-14
bump

---

