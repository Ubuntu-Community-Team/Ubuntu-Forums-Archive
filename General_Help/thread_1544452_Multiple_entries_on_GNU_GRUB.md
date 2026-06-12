---
title: "Multiple entries on GNU GRUB"
date: 2010-08-02
forum: General Help
---

### Post by SkulblakaSama on 2010-08-02
Greetings to everyone, 

I'll get directly to the point, I've installed Ubuntu, Linux on the same partition as Windows 7. Everything works just as it should be, no problems and I'm actually enjoying Ubuntu. ;) It's a nice and clean OS. 

Now, I'm having trouble with the GRUB, since I have updated Ubuntu a few times. It's not a large problem, but I don't like it around. 

I attached a picture of my GRUB, it may take too many words to describe what's going on, so see for yourself. 

A solution would be greatly appreciated.

---

### Post by TeoBigusGeekus on 2010-08-02
[http://ubuntuforums.org/showthread.php?t=1502173]("http://ubuntuforums.org/showthread.php?t=1502173")

---

### Post by SkulblakaSama on 2010-08-02
> **TeoBigusGeekus said:**
> [http://ubuntuforums.org/showthread.php?t=1502173](http://ubuntuforums.org/showthread.php?t=1502173)

Excellent, thank you for your quick reply. :popcorn:

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings,

I had the same problem and the fix was easy. Download and install Ubuntu Tweak. You can get it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

There is a menu entry marked "Package Cleaner". That brings up a screen with a button marked "Clean Kernels". Click that, unlock the screen and mark the checkbox to select all, then clean. That will remove superfluous kernal enteries from the grub menu.

The alternative is to manually remove old kernel packages and update grub, but Ubuntu Tweak may be a safer and more expedient means to the same end.

BTW you may have to run Ubuntu Tweak with root privileges "gksu ubuntu-tweak" or add the "gksu " to the shortcut/launcher properties in the menu editor.
;)

---

### Post by krishnandu.sarkar on 2010-08-02
Wow I was also looking for something like this. Thanks :)

---

### Post by SkulblakaSama on 2010-08-02
> **Maverick_Meerkat said:**
> Greetings,

I had the same problem and the fix was easy. Download and install Ubuntu Tweak. You can get it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

There is a menu entry marked "Package Cleaner". That brings up a screen with a button marked "Clean Kernels". Click that, unlock the screen and mark the checkbox to select all, then clean. That will remove superfluous kernal enteries from the grub menu.

The alternative is to manually remove old kernel packages and update grub, but Ubuntu Tweak may be a safer and more expedient means to the same end.

BTW you may have to run Ubuntu Tweak with root privileges "gksu ubuntu-tweak" or add the "gksu " to the shortcut/launcher properties in the menu editor.
;)

Nice post, that makes things a whole lot easier. :o

---

### Post by giddyup306 on 2010-08-02
> **Maverick_Meerkat said:**
> Greetings,

I had the same problem and the fix was easy. Download and install Ubuntu Tweak. You can get it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

There is a menu entry marked "Package Cleaner". That brings up a screen with a button marked "Clean Kernels". Click that, unlock the screen and mark the checkbox to select all, then clean. That will remove superfluous kernal enteries from the grub menu.

The alternative is to manually remove old kernel packages and update grub, but Ubuntu Tweak may be a safer and more expedient means to the same end.

BTW you may have to run Ubuntu Tweak with root privileges "gksu ubuntu-tweak" or add the "gksu " to the shortcut/launcher properties in the menu editor.
;)

Thanks! I had 31 different boot options!

---

### Post by Maverick_Meerkat on 2010-08-02
> **SkulblakaSama said:**
> Nice post, that makes things a whole lot easier. :o

My pleasure. Glad I could help.

---

