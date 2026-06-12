---
title: "Run one program with different theme"
date: 2012-05-07
forum: General Help
---

### Post by EgoGratis on 2012-05-07
Is it possible to run one program with custom theme? For example default system theme is ambiance and only one program would use radiance theme.

Thanks.

---

### Post by georgelappies on 2012-05-07
> **EgoGratis said:**
> Is it possible to run one program with custom theme? For example default system theme is ambiance and only one program would use radiance theme.

Thanks.

Not sure, not unless you run the second program as a different user using gksu and that user has the radiance theme set as its default...

---

### Post by Helkaluin on 2012-05-07
See this: [https://urukrama.wordpress.com/2008/07/13/setting-a-custom-gtk-theme-for-specific-applications/](https://urukrama.wordpress.com/2008/07/13/setting-a-custom-gtk-theme-for-specific-applications/)

---

### Post by EgoGratis on 2012-05-09
First thanks for answers.

GTK2_RC_FILES=/home/urukrama/.themes/royalty/gtkr-2.0/gtkrc

This does work but i guess it works 100% only for GTK 2 applications and themes and i investigated and if i combine the above command with this command in one single line:

GTK_DATA_PREFIX=/home/urukrama/.themes/royalty/gtkr-3.0/gtk.css

Then i do get better result but still Window Theme is missing.

Question: Does anybody know the name of environment variable to set Window Theme (decorations/borders) too? Or better yet if there is more general environment variable that would work like this:

NAME=/home/urukrama/.themes/royalty name_program

Thanks!

---

