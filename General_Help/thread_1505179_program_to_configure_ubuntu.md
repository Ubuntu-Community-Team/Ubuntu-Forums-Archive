---
title: "program to configure ubuntu"
date: 2010-06-08
forum: General Help
---

### Post by HarmonicaGoldfish on 2010-06-08
About a week ago I installed a program that allowed me to configure ubuntu. For example, I was able to change the window buttons that control maximize/minimize/close from the mac-y kind that automatically come with lucid on the top left of the window back to ubuntu's traditional top right controls. Since then, I installed MoonOS and am now back on Lucid. MoonOS just didn't do it for me.

For the life of me I can not remember where I found out about the program or what it was called! Any ideas?

---

### Post by dewey_daniels on 2010-06-08
Ubuntu Tweak most likely

---

### Post by HarmonicaGoldfish on 2010-06-08
No, it wasn't ubuntu tweak - it's ailurus! I found it while searching for ubuntu tweak. Check it out here:

[http://www.webupd8.org/2010/03/tweak-ubuntu-with-ailurus-10032-just.html](http://www.webupd8.org/2010/03/tweak-ubuntu-with-ailurus-10032-just.html)

Looking forward to getting my window controls back :)

---

### Post by SlidingHorn on 2010-06-09
> **HarmonicaGoldfish said:**
> No, it wasn't ubuntu tweak - it's ailurus! I found it while searching for ubuntu tweak. Check it out here:

[http://www.webupd8.org/2010/03/tweak-ubuntu-with-ailurus-10032-just.html](http://www.webupd8.org/2010/03/tweak-ubuntu-with-ailurus-10032-just.html)

Looking forward to getting my window controls back :)

Well, you can use that program (Ailurus) or give the default that comes w/ Ubuntu a try.  Hit Alt+F2, and type gconf-editor in the box.  Window controls are at: apps > Metacity > general > button_layout.

if you want them on the left, you would edit the value to something like: 

```
minimize,maximize,close:menu
```

or on the right:

```
menu:minimize,maximize,close
```

If you just want to change the look (not the location) of the controls, you would do that with your theme chooser/editor by going to your Menu > System > Preferences > Appearance and making your changes there.

---

### Post by pizza-is-good on 2010-06-09
wow, I had been using Ubuntu Tweak, but reading this made me want to try  ailurus. It is very nice. It is not a complete replacement of UT, but a nice addition. or maybe UT is a nice addition to ailurus..

---

