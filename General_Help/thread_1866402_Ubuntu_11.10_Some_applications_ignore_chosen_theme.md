---
title: "Ubuntu 11.10: Some applications ignore chosen theme"
date: 2011-10-21
forum: General Help
---

### Post by veroslav on 2011-10-21
Hi,

I have a small theme related issue in Ubuntu 11.10. I have used Gnome Tweak Tool to set icon, window and GTK+ theme to Adwaita. In some applications, such as gEdit, everything looks good, the theme is applied correctly.

However, for most of the others, such as Deluge, the buttons, highlighting colors and other components, do not use the new theme, but seem to use an older looking one (reminds me of Clearlooks theme).

I've attached screenshots of both gEdit and Deluge after applying Adwaita theme; notice the difference in button and checkbox layout and also the difference in the highlighting color.

Is there any reason for this behaviour? How can I fix it, if possible?

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by vasa1 on 2011-10-21
Not helpful but it seems something similar is here:
[http://ubuntuforums.org/showthread.php?t=1866217](http://ubuntuforums.org/showthread.php?t=1866217)

---

### Post by veroslav on 2011-10-21
Yeah, I saw that thread earlier, although it does appear that it applies to Xubuntu only.

Thanks anyway! :)

I will still wait and appreciate if anyone has any other suggestions.

Regards,
Veroslav

---

### Post by vasa1 on 2011-10-21
> **veroslav said:**
> Yeah, I saw that thread earlier, although it does appear that it applies to Xubuntu only.
...

From what I gather, it's broader than Xubuntu. It seems that some apps are gtk-3 "ready" for want of a better word. Others aren't. Unfortunately, there's not much information forthcoming and one has to scrounge for crumbs.

If one is prepared to wait, it's quite possible that there'll be a properly formulated solution:
> In addition to that, the designers and developers figured that it’s better to care about getting the fundamentals done right first, **and allowing for more superficial concerns such as theming later**.
from: [http://piecesoflint.wordpress.com/2011/04/06/how-to-tweak-gnome-3-to-your-needs/](http://piecesoflint.wordpress.com/2011/04/06/how-to-tweak-gnome-3-to-your-needs/)

In the meanwhile, I'm (quite unexpectedly) having the time of my life editing .css files and gtkrc following the sacred principles of trial and error.

---

### Post by veroslav on 2011-10-21
Thank you for the explaination, I really appreciate it. I understand the reasons for this issue better now, and it really does not matter that much. As you said, I am really enjoying other aspects of this release and I am very satisfied.

I will patiently wait until this is fixed.

Thanks again.

/Veroslav

---

### Post by fragos on 2011-10-21
I have the same issue with a dark version of that theme. It appears that it calls out colors differently for gtk 2.0 and gtk 3.0. True Gnome aps like Gedit and Nautilus have changed to gtk 3.0 but some of the others like Midori still use gtk 2.0. The Ambiance theme that 11.10 defaults to doesn't do that.

---

### Post by bodhi.zazen on 2011-10-21
See also 

[http://blog.bodhizazen.net/linux/using-gtk-2-themes-with-qt-applications/](http://blog.bodhizazen.net/linux/using-gtk-2-themes-with-qt-applications/)

to theme qt applications (virtualbox, etc).

---

### Post by vasa1 on 2011-10-21
> **fragos said:**
> ...The Ambiance theme that 11.10 defaults to doesn't do that.

Hi! Could you please clarify this? Is it correct to understand that if one uses the "Ambiance" theme, many, if not all, programs will be similarly themed, even things like LibreOffice?

---

### Post by fragos on 2011-10-21
> **vasa1 said:**
> Hi! Could you please clarify this? Is it correct to understand that if one uses the "Ambiance" theme, many, if not all, programs will be similarly themed, even things like LibreOffice?

That appears to be the case, particularly compared to "Adwaita." If you examine the theme files in /usr/share/themes you'll see that gtk 2.0 and gtk 3.0 have separate theme definitions. In the case of "Ambiance" the colors are specified the same for both.

---

### Post by vasa1 on 2011-10-21
> **fragos said:**
> That appears to be the case, particularly compared to "Adwaita." If you examine the theme files in /usr/share/themes you'll see that gtk 2.0 and gtk 3.0 have separate theme definitions. In the case of "Ambiance" the colors are specified the same for both.

Thanks for that. Maybe, I should switch to Ambiance so that I've to worry about just one "gtk" :D

I thought I was playing safe by going with Adwaita since that's the GNOME default. But I guess it makes more sense sticking to Ubuntu/Unity's default.

---

### Post by veroslav on 2011-10-23
Just wanted to share this:

I installed the following theme:

[http://gnome-look.org/content/show.php?content=142247](http://gnome-look.org/content/show.php?content=142247)

and then applied it in Gnome Tweak Tool (Theme->Gtk+ Theme). It fixes the problem I described in my original post.

I thought it might be good to know.

Kind Regards,
Veroslav

---

