---
title: "nautilus action configuration not running"
date: 2010-03-30
forum: General Help
---

### Post by jsriz on 2010-03-30
I recently installed nautilus-actions for adding things to the right click menu 
this shows the Nautilus Actions Configuration in system->preferences 
but when i click it nothing happens 
I then try to run it from the terminal by running the "nautilus-actions-config-tool " command it returns 
```

Gtk-Message: Failed to load module "rgba": librgba.so: cannot open shared object file: No such file or directory
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:173: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:214: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:320: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:327: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:341: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:363: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:365: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:389: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:395: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:434: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:440: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:517: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:550: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:552: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:571: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:572: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:606: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:607: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:647: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:649: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:672: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:674: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:706: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:707: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:721: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:722: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:741: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:743: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:772: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:775: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:791: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:807: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:830: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:871: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:878: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:897: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:904: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:943: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:945: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:990: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:997: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1181: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1184: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1269: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1276: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1313: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1315: Murrine configuration option "profile" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1330: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/srinivas/.themes/Impression/gtk-2.0/gtkrc:1335: Murrine configuration option "profile" is no longer supported and will be ignored.

(nautilus-actions-config-tool:6132): NA-nact-CRITICAL **: get_actions_list_treeview: assertion `GTK_IS_TREE_VIEW( treeview )' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_tree_selection_set_mode: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(nautilus-actions-config-tool:6132): NA-nact-CRITICAL **: get_actions_list_treeview: assertion `GTK_IS_TREE_VIEW( treeview )' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_label_set_mnemonic_widget: assertion `GTK_IS_LABEL (label)' failed

(nautilus-actions-config-tool:6132): NA-nact-CRITICAL **: nact_tree_model_initial_load: assertion `GTK_IS_TREE_VIEW( treeview )' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_tree_view_set_enable_tree_lines: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_combo_box_set_model: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_combo_box_entry_get_text_column: assertion `GTK_IS_COMBO_BOX_ENTRY (entry_box)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_cell_layout_clear: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_cell_layout_pack_start: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_cell_layout_add_attribute: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_cell_layout_pack_start: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_cell_layout_add_attribute: assertion `GTK_IS_CELL_LAYOUT (cell_layout)' failed

(nautilus-actions-config-tool:6132): Gtk-CRITICAL **: gtk_combo_box_set_active: assertion `GTK_IS_COMBO_BOX (combo_box)' failed
**
NA-nact:ERROR:nact-ibackground-tab.c:381:get_folders_treeview: assertion failed: (GTK_IS_TREE_VIEW( treeview ))
Aborted (core dumped)

```How can I get this tool running???

---

### Post by 2hot6ft2 on 2010-03-30
First all those errors look like a theme issue. Change the theme and try.
Some themes may appear or look ok but they written before some things changed or weren't written properly so they cause issues like that.

The command it would run from the menu is
```
nautilus-actions-config
```
not
```
nautilus-actions-config-tool
```
Maybe that would help too.

---

