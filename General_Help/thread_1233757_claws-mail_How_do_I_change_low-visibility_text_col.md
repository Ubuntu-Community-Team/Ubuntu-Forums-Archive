---
title: "claws-mail: How do I change low-visibility text colors"
date: 2009-08-07
forum: General Help
---

### Post by Siúlóir on 2009-08-07
Since upgrading to Jaunty the text color in the summary and folder panes of Claws-Mail is low-visibility gray-on-white. The color in the message pane is black-on-white which also was the color combination of the other panes in Intrepid.

How can I change that? 

In the Preferences menu I only found settings for colors relating to the quoting style or text font settings.

Cheers

Siúlóir

---

### Post by alfplayer on 2009-08-09
The text color in the summary and folder panes is set by the GTK configuration, which is set by the Ubuntu theme. You can try starting Claws after setting a theme with dark fonts.

If you want to fix this problem without changing the theme you can see this thread to change the GTK theme used by Claws only: [http://ubuntuforums.org/showthread.php?t=552074](http://ubuntuforums.org/showthread.php?t=552074)

---

### Post by Siúlóir on 2009-08-09
> **alfplayer said:**
> The text color in the summary and folder panes is set by the GTK configuration, which is set by the Ubuntu theme. You can try starting Claws after setting a theme with dark fonts.

Thanks! I now call a script instead of invoking claws-mail directly:

```
#!/bin/sh
export GTK2_RC_FILES=/home/jmf/.gtkrc/gtkrc.claws-mail
/usr/bin/claws-mail
```

---

