---
title: "Broken Open Office GUI"
date: 2006-04-26
forum: General Help
---

### Post by Amiel on 2006-04-26
I just logged into Ubuntu again after a while and was greeted by an Open Office Writer that looked like this, the icons and text like to vanish randomly when hovered over. Sometimes they'll be back but when I move my mouse over them, they'll vanish again. Does anyone happen to know what could have gone wrong? This has never happened to me before. All other applications seem to be behaving normally. I tried reinstalling the program and wiping the hidden preferences folder in my home directory, which didn't help. Any ideas? Thanks a lot in advance.

[[IMG]http://img267.imageshack.us/img267/4126/screenshot5yu.th.png[/IMG]](http://img267.imageshack.us/my.php?image=screenshot5yu.png)

Oh, yeah, it happens in all OO applications, by the way.

---

### Post by Qrk on 2006-04-26
I have an idea, try uninstalling the package *openoffice.org-gtk-gnome*. This will force openoffice to use it's own widget set, which might not have the same problem you've had. 

Its worth a shot.

---

### Post by Amiel on 2006-04-26
[QUOTE=Qrk]I have an idea, try uninstalling the package *openoffice.org-gtk-gnome*. This will force openoffice to use it's own widget set, which might not have the same problem you've had. 

Its worth a shot.[/QUOTE]
Thanks for the tip, that worked but Open Office looks horrible now. Oh well.

---

### Post by nanotube on 2006-04-26
[QUOTE=Amiel]Thanks for the tip, that worked but Open Office looks horrible now. Oh well.[/QUOTE]
well, try reinstalling that gtk package, and maybe that will fix your problem :)

---

