---
title: "What do you do with a patch?"
date: 2011-08-21
forum: General Help
---

### Post by whatthefunk on 2011-08-21
Sorry for the noob question, but Ive always wondered this.  A lot of times when you report a bug, one of the developers will post a patch, but I usually dont know what to do with it.  For example, this patch from the Lubuntu mailing list:
```
--- a/src/desktop-ui.c	2010-10-15 10:26:53.000000000 +0200
+++ b/src/desktop-ui.c	2011-08-12 12:37:56.279733976 +0200
@@ -26,6 +26,7 @@ static const char desktop_menu_xml[] =
   "<menu action='CreateNew'>"
     "<menuitem action='NewFolder'/>"
     "<menuitem action='NewBlank'/>"
+    "<menuitem action='NewShortcut'/>"
   "</menu>"
   "<separator/>"
   "<menuitem action='Paste'/>"
@@ -55,6 +56,7 @@ static const GtkActionEntry desktop_acti
     {"CreateNew", GTK_STOCK_NEW, N_("_New"), "", NULL, NULL},
     {"NewFolder", "folder", N_("Folder"), "<Ctrl><Shift>N", NULL, G_CALLBACK(on_create_new)},
     {"NewBlank", "text-x-generic", N_("Blank File"), NULL, NULL, G_CALLBACK(on_create_new)},
+    {"NewShortcut", "system-run", N_("Shortcut"), NULL, NULL, G_CALLBACK(on_create_new)},
     {"Prop", GTK_STOCK_PROPERTIES, N_("Desktop Preferences"), "<Alt>Return", NULL, G_CALLBACK(fm_desktop_preference)}
 };
 
--- a/src/desktop.c	2011-08-12 13:20:45.000000000 +0200
+++ b/src/desktop.c	2011-08-12 12:40:07.370541766 +0200
@@ -2002,6 +2002,8 @@ void on_create_new(GtkAction* act, gpoin
         name = TEMPL_NAME_FOLDER;
     else if( strcmp(name, "NewBlank") == 0 )
         name = TEMPL_NAME_BLANK;
+    else if( strcmp(name, "NewShortcut") == 0)
+        name = TEMPL_NAME_SHORTCUT;
     pcmanfm_create_new(NULL, fm_path_get_desktop(), name);
 }
 
--- a/src/main-win-ui.c	2010-10-15 10:26:53.000000000 +0200
+++ b/src/main-win-ui.c	2011-08-12 13:07:28.554932704 +0200
@@ -100,6 +100,7 @@ static const char main_menu_xml[] =
   "<menu action='CreateNew'>"
     "<menuitem action='NewFolder'/>"
     "<menuitem action='NewBlank'/>"
+    "<menuitem action='NewShortcut'/>"
   "</menu>"
   "<separator/>"
   "<menuitem action='Paste'/>"
@@ -171,6 +172,7 @@ static GtkActionEntry main_win_actions[]
     {"CreateNew", GTK_STOCK_NEW, N_("_New"), "", NULL, NULL},
     {"NewFolder", "folder", N_("Folder"), "<Ctrl><Shift>N", NULL, G_CALLBACK(on_create_new)},
     {"NewBlank", "text-x-generic", N_("Blank File"), NULL, NULL, G_CALLBACK(on_create_new)},
+    {"NewShortcut", "system-run", N_("Shortcut"), NULL, NULL, G_CALLBACK(on_create_new)},
     {"Prop", GTK_STOCK_PROPERTIES, NULL, NULL, NULL, G_CALLBACK(on_prop)}
 };

--- a/src/main-win.c	2011-08-12 13:20:45.000000000 +0200
+++ b/src/main-win.c	2011-08-12 15:00:27.662364700 +0200
@@ -1262,6 +1262,8 @@ void on_create_new(GtkAction* action, Fm
         name = TEMPL_NAME_FOLDER;
     else if( strcmp(name, "NewBlank") == 0 )
         name = TEMPL_NAME_BLANK;
+    else if( strcmp(name, "NewShortcut") == 0 )
+        name = TEMPL_NAME_SHORTCUT;
     pcmanfm_create_new(GTK_WINDOW(win), fm_folder_view_get_cwd(fv), name);
 }

--- a/src/pcmanfm.h	2010-10-15 10:26:53.000000000 +0200
+++ b/src/pcmanfm.h	2011-08-12 15:19:38.503970818 +0200
@@ -44,6 +44,7 @@ void pcmanfm_open_folder_in_terminal(Gtk
 
 #define TEMPL_NAME_FOLDER    NULL
 #define TEMPL_NAME_BLANK     (const char*)-1
+#define TEMPL_NAME_SHORTCUT  (const char*)-2
 void pcmanfm_create_new(GtkWindow* parent, FmPath* cwd, const char* templ);
 
 G_END_DECLS


--- a/src/pcmanfm.c	2011-08-12 13:20:45.000000000 +0200
+++ b/src/pcmanfm.c	2011-08-12 15:25:46.655997442 +0200
@@ -607,6 +607,15 @@ _retry:
         }
         g_object_unref(gf);
     }
+    else if ( templ == TEMPL_NAME_SHORTCUT )
+    {
+      char buf[256];
+      GFile* gf = fm_path_to_gfile(dest);
+      printf("Creating Shortcut..."); // Debug message
+      sprintf(buf, "/usr/bin/lxshortcut -i %s",g_file_get_path(gf));
+      system(buf);
+      g_object_unref(gf);
+    }
     else /* templates in ~/Templates */
     {
         FmPath* dir = fm_path_new_for_str(g_get_user_special_dir(G_USER_DIRECTORY_TEMPLATES));
```

[https://lists.launchpad.net/lubuntu-desktop/msg04582.html](https://lists.launchpad.net/lubuntu-desktop/msg04582.html)

What do I do with this?

---

