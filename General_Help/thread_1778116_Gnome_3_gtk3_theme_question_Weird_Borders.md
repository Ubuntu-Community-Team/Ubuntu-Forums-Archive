---
title: "Gnome 3 gtk3 theme question: Weird Borders"
date: 2011-06-08
forum: General Help
---

### Post by andrewk36 on 2011-06-08
So after properly installing the Atolm gtk3 theme by half-left in Gnome 3 (which I installed in Ubuntu using the gnome3team ppa), I noticed weird borders around buttons, and I'm wondering how I can fix them. Any suggestions?

I already tried loging out/in, restarting shell and rebooting, btw.

[http://i.stack.imgur.com/M1aYa.png](http://i.stack.imgur.com/M1aYa.png)

Edit: fixed image link/size

---

### Post by cbowman57 on 2011-06-08
> **andrewk36 said:**
> So after properly installing the Atolm gtk3 theme by half-left in Gnome 3 (which I installed in Ubuntu using the gnome3team ppa), I noticed weird borders around buttons, and I'm wondering how I can fix them. Any suggestions?

I already tried loging out/in, restarting shell and rebooting, btw.

[http://i.stack.imgur.com/M1aYa.png](http://i.stack.imgur.com/M1aYa.png)

Edit: fixed image link/size

Try downgrading gnome-themes-standard.  If you can't get it fixed (it's a bug), & want that dark theme Adwaita dark isn't bad.  To use that just navigate to /usr/share/themes/Adwaita/gtk-3.0 & rename gtk-dark.css to gtk.css.

---

### Post by andrewk36 on 2011-06-08
Hmm what seems strange to me is that I also have the Zukitwo gtk3 theme installed and when I switch to that one, it works without those weird ugly button borders. So the bug only applies to the Atolm Theme. 

And is the reason I should downgrade gnome-themes-standard because I may have too recent of a version? (testing version?)

---

### Post by cbowman57 on 2011-06-08
> **andrewk36 said:**
> Hmm what seems strange to me is that I also have the Zukitwo gtk3 theme installed and when I switch to that one, it works without those weird ugly button borders. So the bug only applies to the Atolm Theme. 

And is the reason I should downgrade gnome-themes-standard because I may have too recent of a version? (testing version?)

Not exactly certain, the bug seems to affect the dark themes the most, but I've seen it happen in a couple of the lighter ones. On my system the gnome-themes-standard from ricotz seemed to introduce that problem, I forced a downgrade & it seemed to fix it, I'm running the Atolm-gtk3 without a problem now.

---

### Post by andrewk36 on 2011-06-08
Hmm I see... Well I'll give the downgrade a shot. Forgot I was also using ricotz ppa and that it had testing packages haha.


Edit: Alright, the downgrade worked, thanks! I wonder what happened that broke the theme in the new version of the standard themes?

---

### Post by cbowman57 on 2011-06-08
> **andrewk36 said:**
> Hmm I see... Well I'll give the downgrade a shot. Forgot I was also using ricotz ppa and that it had testing packages haha.

Yeah, I just turn it on to get the network-manager (I think) then deactivate it.  There might be a couple other packages he has that are needed, but he warned us personally to be cautious using his ppa.

---

### Post by andrewk36 on 2011-06-08
Alright, yeah I gotta be more careful about that ppa. Thanks for the solution!

---

### Post by cbowman57 on 2011-06-08
Cheers!  :)

---

### Post by LarsKongo on 2011-06-09
It's a new feature in the Adwaita engine. Some themes just haven't been updated. It can be fixed by adding this to gtk-widgets.css:

```
* {
	-adwaita-inset-left: none;
	-adwaita-inset-right: none;
	-adwaita-inset-top: none;
	-adwaita-inset-bottom: none;
}
```

---

### Post by cbowman57 on 2011-06-09
> **LarsKongo said:**
> It's a new feature in the Adwaita engine. Some themes just haven't been updated. It can be fixed by adding this to gtk-widgets.css:

```
* {
	-adwaita-inset-left: none;
	-adwaita-inset-right: none;
	-adwaita-inset-top: none;
	-adwaita-inset-bottom: none;
}
```

Ok, this should be inserted into the gtk-widgets.css of every theme?  And where exactly in the file should it be inserted?

---

### Post by LarsKongo on 2011-06-09
It should be added to all of the themes that does have this pink border problem. It doesn't matter where in the css file you put it. '*' means to apply it to all widgets by default.

An other option would be to contact the theme developer to update the theme with this.

---

### Post by cbowman57 on 2011-06-09
@LarsKongo; thank you for that information. Editing now. ;)

---

