---
title: "Restore Login Screen UI"
date: 2010-04-14
forum: General Help
---

### Post by bolenjx1 on 2010-04-14
i just installed Ubuntu 9.10 today and got the regular login screen like this:

[http://www.linuxtutorial.it/wp-content/ubuntu_karmic23.png](http://www.linuxtutorial.it/wp-content/ubuntu_karmic23.png)

But I was tinkering around while I was there and hit the accessibility button, chose one of the options that had something to do with contrast then the UI changed colors and became Blue and white-ish. I unchecked the contrast option again but the UI didn't change back to its original colors like the image above. Rebooting didn't work either.

Anyone know how to fix this?

---

### Post by ttshivers on 2010-04-14
When you log in does it look like the attached picture or something close to it or is the wierd theme only on the login screen?

If so, then you need to change your theme.  To do that:

1. Right click on the desktop
2. Select: change desktop background
3. Click on the themes tab
4. Select the "Human" theme (which is the defualt ubuntu theme)

That should do it

---

### Post by bolenjx1 on 2010-04-14
The weird theme happens only in the login screen. I'm not sure why it didn't revert back to the old one when I unchecked that accessibility option. My desktop is perfectly fine. Oh yeah, it's called "enhance contrast in colors" or something like that.

---

### Post by ttshivers on 2010-04-14
In attempting to help you, I did the same thing you did, and I now have the same problem as you.  :(

---

### Post by bolenjx1 on 2010-04-14
My apologies for that.. Could it be a bug perhaps :(

---

### Post by ttshivers on 2010-04-14
I don't know.  I have seen different articles about how the login screen can't really be customized in Ubuntu 9.10.  I really don't know much about it though.

---

### Post by bolenjx1 on 2010-04-15
ok, I think I fixed it.

You need to install the GDM2 config tool from here: [http://ubuntuforums.org/showthread.php?t=1358026](http://ubuntuforums.org/showthread.php?t=1358026)

Go to System > Admin > Login Screen(GDM2 Setup) > Decoration

For GTK Theme choose HumanLogin
For Icon Theme choose HumanLoginIcons

---

### Post by ttshivers on 2010-04-15
Thanks.  Now I can fix it too. :-)

---

