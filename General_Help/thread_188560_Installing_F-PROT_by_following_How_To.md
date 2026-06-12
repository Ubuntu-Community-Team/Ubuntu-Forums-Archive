---
title: "Installing F-PROT by following How To"
date: 2006-06-04
forum: General Help
---

### Post by IsKall on 2006-06-04
I recently tried to follow this instruction 

```
http://ubuntuforums.org/showthread.php?t=88357
```

 but "sudo checkinstall" fails:


I only took the last bit of the errors:

```

xfprot-gtk.c:1237: warning: implicit declaration of function ‘gtk_radio_button_get_group’
xfprot-gtk.c:1237: warning: implicit declaration of function ‘GTK_RADIO_BUTTON’
xfprot-gtk.c:1262: warning: implicit declaration of function ‘gtk_tooltips_new’
xfprot-gtk.c:1277: warning: implicit declaration of function ‘gtk_tooltips_set_tip’
xfprot-gtk.c:1277: warning: implicit declaration of function ‘GTK_TOOLTIPS’
xfprot-gtk.c:1290: warning: implicit declaration of function ‘gtk_tooltips_enable’
xfprot-gtk.c:1407: warning: implicit declaration of function ‘gtk_widget_show_all’
xfprot-gtk.c:1411: warning: implicit declaration of function ‘gtk_events_pending’
xfprot-gtk.c:1412: warning: implicit declaration of function ‘gtk_main_iteration’
make: *** [xfprot-gtk.o] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```


Anyone who can help me?

---

### Post by givré on 2006-06-04
Could you put a bit more of the errors you had please, we could see only the warning there (which are not important), but not the error mention at the end.

---

