---
title: "I like my dark theme but not my dark open office"
date: 2009-12-02
forum: General Help
---

### Post by hockeyhead019 on 2009-12-02
hey guys,

well as the thread implies i have a dark theme which i like, however i do not like the way office is set up... so is there any way to apply a separate theme to open office? even if it is just the standard theme?

thanks

-Jim

---

### Post by sisco311 on 2009-12-04
```
GTK2_RC_FILES="/usr/share/themes/Human/gtk-2.0/gtkrc" ooffice -writer
```

Right click on the Application menu -> Edit menus -> Office -> highlight Openoffice.org Word Processor -> Properties and replace the command with:
```
bash -c "GTK2_RC_FILES="/usr/share/themes/Human/gtk-2.0/gtkrc" ooffice -writer %F"
```

---

### Post by Hagar Delest on 2009-12-05
See also that post: [Re: Dark theme makes OpenOffice unusable!]("http://ubuntuforums.org/showpost.php?p=5838281&postcount=17"). It points to a site that will explain how to do it. I just tried on my xubuntu Karmic box and it works like a charm. I had to edit slightly the path and my **openoffice.org3** file in /usr/bin has for second line:
exec env GTK2_RC_FILES=/usr/share/themes/Industrial/gtk-2.0/gtkrc /opt/openoffice.org3/program/soffice "$@"

NB: I then launch OOo with the command /usr/bin/openoffice.org3 (it's the start center).

---

### Post by Hagar Delest on 2010-02-06
See that one (especially the end), it even brings back the default gray shading: [[Solved] OOO_FORCE_DESKTOP for dark themes]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=27216").

---

