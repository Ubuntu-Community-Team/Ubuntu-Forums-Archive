---
title: "evince annotation problem"
date: 2011-05-22
forum: General Help
---

### Post by evan54 on 2011-05-22
I open a .pdf from the terminal as follows:

evince pdffile.pdf

When I add an annotation and then close the yellow box I get a series of messages in the terminal that just go on forever... I wouldn't be so worried but when I click on the sticky note it doesn't re open the annotation box with the text hence this post. Any ideas why this is happening?


Messages that are spit out in the terminal:

(evince:2202): Gtk-CRITICAL **: IA__gtk_widget_get_visible: assertion `GTK_IS_WIDGET (widget)' failed

(evince:2202): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

thanks

===== UPDATE =====

This problem only appears if I use alt+f4 to close the yellow box. If I use the "x" on the top right corner of the yellow box to close it there is no problem.

---

