---
title: "Compiling Gnome-Shell from GIT (error)"
date: 2011-01-22
forum: General Help
---

### Post by dmaxel on 2011-01-22
I'm trying to compile Gnome-Shell to try it out, but I run into this problem:
```
make[5]: Leaving directory `/home/dmaxel/gnome-shell/source/gnome-settings-daemon/plugins/media-keys/cut-n-paste'
make[5]: Entering directory `/home/dmaxel/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
  CC     libmedia_keys_la-gsd-media-keys-plugin.lo
  CC     libmedia_keys_la-gsd-media-keys-manager.lo
  CC     libmedia_keys_la-gsd-media-keys-window.lo
  CC     libmedia_keys_la-gsd-marshal.lo
  CCLD   libmedia-keys.la
  CC     test_media_keys-gsd-media-keys-manager.o
  CC     test_media_keys-gsd-media-keys-window.o
  CC     test_media_keys-test-media-keys.o
  CC     test_media_keys-gsd-marshal.o
  CCLD   test-media-keys
/home/dmaxel/gnome-shell/install/lib/libgtk-3.0.so: undefined reference to `g_source_get_time'
/home/dmaxel/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/home/dmaxel/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/dmaxel/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/home/dmaxel/gnome-shell/install/lib/libgtk-3.0.so: undefined reference to `g_list_free_full'
/home/dmaxel/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/home/dmaxel/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/home/dmaxel/gnome-shell/install/lib/libgtk-3.0.so: undefined reference to `g_get_monotonic_time'
/home/dmaxel/gnome-shell/install/lib/libgdk-3.0.so: undefined reference to `g_slist_free_full'
collect2: ld returned 1 exit status
make[5]: *** [test-media-keys] Error 1
make[5]: Leaving directory `/home/dmaxel/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/dmaxel/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/dmaxel/gnome-shell/source/gnome-settings-daemon/plugins/media-keys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dmaxel/gnome-shell/source/gnome-settings-daemon/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dmaxel/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [27/33]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 

```What do I need to do?

---

### Post by atomic0x on 2011-01-24
I had the exact same issue. I followed the instructions at [http://live.gnome.org/GnomeShell/RemovingLaFiles](http://live.gnome.org/GnomeShell/RemovingLaFiles) to clean up some libraries with hard-coded paths.

The downside is that you have to start compiling all over again, but it does complete.

---

