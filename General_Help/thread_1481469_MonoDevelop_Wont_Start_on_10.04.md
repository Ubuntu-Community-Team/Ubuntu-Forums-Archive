---
title: "MonoDevelop Wont Start on 10.04"
date: 2010-05-12
forum: General Help
---

### Post by oneadvent on 2010-05-12
I installed the program from apt-get and this is what I get:

```
oneadvent@oneadvent-laptop:~$ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.
```

and then nothing more, I left it running for like 10 minutes and still the splash screen but no program.

Any help would be appreciated.

---

### Post by oneadvent on 2010-05-12
bump

any ideas? am I in the wrong forum?

---

### Post by eznet on 2010-05-30
I too am curious about this error. 

```
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

```

Oddly, MonoDevelop will load on my 10.04 box, but a lot of things seem not to work...  The "Generate Data Classes" for database connections will not work...  Get:

```
WARNING [2010-05-30 19:43:54Z]: Gtk-Warning: /build/buildd/gtk+2.0-2.20.0/gtk/gtktreestore.c:765: Unable to convert from GtkSharpValue to gchararray

Stack trace: 
   at Gtk.TreeStore.SetValue(TreeIter iter, Int32 column, Value value)
   at Gtk.TreeStore.SetValue(TreeIter iter, Int32 column, System.Object value)
   at Gtk.TreeStore._AppendValues(TreeIter iter, System.Array values)
   at Gtk.TreeStore.AppendValues(System.Array values)
   at Gtk.TreeStore.AppendValues(System.Object[] values)
   at MonoDevelop.Database.Components.ProjectDirectoryComboBox.PopulateCombo()
   at MonoDevelop.Database.Components.ProjectDirectoryComboBox..ctor()
   at MonoDevelop.Database.CodeGenerator.GenerateDataClassesDialog..ctor()
   at MonoDevelop.Database.CodeGenerator.GenerateDataClassesHandler.Run()
   at MonoDevelop.Components.Commands.CommandHandler.Run(System.Object dataItem)
   at MonoDevelop.Components.Commands.ActionCommand.DispatchCommand(System.Object dataItem)
   at MonoDevelop.Components.Commands.CommandManager.DispatchCommand(System.Object commandId, System.Object dataItem, System.Object initialTarget)
   at MonoDevelop.Components.Commands.CommandMenuItem.OnActivated()
   at Gtk.MenuItem.activated_cb(IntPtr menu_item)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at MonoDevelop.Ide.Gui.IdeApp.Run()
   at MonoDevelop.Ide.Gui.IdeStartup.Run(System.String[] args)
   at MonoDevelop.Startup.MonoDevelopMain.Main(System.String[] args)
ERROR [2010-05-30 19:43:54Z]: Gtk-Critical: gtk_tree_view_column_cell_layout_set_cell_data_func: assertion `info != NULL' failed
Stack trace: 
   at Gtk.TreeViewColumn.SetCellDataFunc(Gtk.CellRenderer cell, Gtk.CellLayoutDataFunc func)
   at MonoDevelop.Database.Components.ColumnMappingWidget..ctor(Boolean showCheckBoxes)
   at MonoDevelop.Database.CodeGenerator.GenerateDataClassesDialog..ctor()
   at MonoDevelop.Database.CodeGenerator.GenerateDataClassesHandler.Run()
   at MonoDevelop.Components.Commands.CommandHandler.Run(System.Object dataItem)
   at MonoDevelop.Components.Commands.ActionCommand.DispatchCommand(System.Object dataItem)
   at MonoDevelop.Components.Commands.CommandManager.DispatchCommand(System.Object commandId, System.Object dataItem, System.Object initialTarget)
   at MonoDevelop.Components.Commands.CommandMenuItem.OnActivated()
   at Gtk.MenuItem.activated_cb(IntPtr menu_item)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at MonoDevelop.Ide.Gui.IdeApp.Run()
   at MonoDevelop.Ide.Gui.IdeStartup.Run(System.String[] args)
   at MonoDevelop.Startup.MonoDevelopMain.Main(System.String[] args)
```

I wish I could find someplace to get the source to build this or instructions to point me otherwise...  Chasing a lot of leads that end in dead ends...

---

