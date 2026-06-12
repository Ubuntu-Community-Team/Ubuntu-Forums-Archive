---
title: "Screem error"
date: 2009-09-22
forum: General Help
---

### Post by kestrel1 on 2009-09-22
Been running screem html editor & it has worked fine for a while now.
Anyway, used it once this evening & it was fine. Closed it down & reopened about 10 minutes later & nothing. The splash screen starts, but the program does not appear. I tried running from the console & got the following:
```
(screem:4421): Gtk-WARNING **: Refusing to add non-unique action 'cancel drag' to action group 'ScreemActions'

(screem:4421): screem-CRITICAL **: screem_page_is_feature: assertion `SCREEM_IS_PAGE( page )' failed

(screem:4421): screem-CRITICAL **: screem_page_is_xml: assertion `SCREEM_IS_PAGE( page )' failed
FAILED TO LOAD
Segmentation fault
```
I tried re-installing, but this made no difference. Did a complete removal & re-install, still the same.
Any ideas?
Thanks

---

### Post by kestrel1 on 2009-09-23
Anyone?

---

### Post by kestrel1 on 2009-09-25
no one got any ideas?

---

### Post by kestrel1 on 2009-10-11
Okay, I sorted it myself. Did a complete removal of Screem & removed the .screem folder from my home directory. Re-installed screem & it now works.

---

### Post by jervin2 on 2009-11-25
I seem to be having the same problem, I did the complete removal, delete the .screem subdir in my home, and reinstall.  No Change.  When I bring it up in a windows I get the following:

(screem:9940): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(screem:9940): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(screem:9940): Gtk-WARNING **: Refusing to add non-unique action 'cancel drag' to action group 'ScreemActions'

(screem:9940): screem-CRITICAL **: screem_page_is_feature: assertion `SCREEM_IS_PAGE( page )' failed

(screem:9940): screem-CRITICAL **: screem_page_is_xml: assertion `SCREEM_IS_PAGE( page )' failed

(screem:9940): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed

---

