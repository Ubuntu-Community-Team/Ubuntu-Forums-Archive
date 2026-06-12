---
title: "cant compile kazehakase browser"
date: 2010-10-19
forum: General Help
---

### Post by termin on 2010-10-19
i downloaded the browser, the ./configure came out fine, but when i did the make it came out as:
  LINK  libkzwidget.la
Making all in prefs_ui
  CC    prefs_entry.o
  CC    prefs_external_program.o
  CC    prefs_font.o
  CC    prefs_general.o
  CC    prefs_gesture.o
  CC    prefs_history.o
  CC    prefs_key_accel.o
  CC    prefs_lang.o
  CC    prefs_tab.o
  CC    prefs_privacy.o
  CC    prefs_proxy.o
  CC    prefs_ui_editor.o
  CC    prefs_bookmark.o
  CC    prefs_browser.o
  LINK  libkzprefsui.la
Making all in sidebar
  CC    kz-bookmarks-sidebar.o
  CC    kz-downloader-sidebar.o
  CC    kz-tabtree.o
kz-tabtree.c:88: error: expected declaration specifiers or ‘...’ before ‘GtkNotebookPage’
kz-tabtree.c:699: error: expected declaration specifiers or ‘...’ before ‘GtkNotebookPage’


there was alot before that, but that was without any error messages, any help?
thanks!

---

### Post by termin on 2010-10-28
i know this is a old thread, but i need to find the fix too, so even though is is monthes old, its still an issue and it needs to be fixed

---

### Post by Zill on 2010-10-28
> **termin said:**
> i know this is a old thread, but i need to find the fix too, so even though is is monthes old, its still an issue and it needs to be fixed
Why compile?  [Kazehakase (0.5.8-1ubuntu1]("http://packages.ubuntu.com/karmic/kazehakase") is in karmic and *may* run OK on later versions of Ubuntu.  I would try adding the karmic universe repository to the sources list, install Kazehakase and then remove the karmic repository to leave the sources list as it was originally.

---

