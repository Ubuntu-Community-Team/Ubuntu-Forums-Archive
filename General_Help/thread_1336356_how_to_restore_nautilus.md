---
title: "how to restore nautilus"
date: 2009-11-24
forum: General Help
---

### Post by thedoommaker on 2009-11-24
well nautilus is messed up completely
here's how I did it
first I changed the trash icon to another one
I found the default icon in the humanity icon pack 
and restored it back but this time the trash icon would still show empty although it isn't empty, it would always show an emty icon on the desktop
then I opened up the configuration editor 
and saw nautilus>desktop>show trash icon was checked 
I changed the value for trash_icon_name to 0 
and finally nautilus was messed up altogether
icons on desktop were gone but panels were fine 
typed nautilus in terminal but nothing happened
typed sudo nautilus, then nautilus showed up and desktop icons (just the drive icons) came back, closed the terminal and they also were gone
is there a way to restore nautilus
or the value for trash_icon_name if that's the main reason for all this?

---

### Post by jerrrys on 2009-11-24
sudo apt-get remove --purge nautilus && sudo apt-get install nautilus

this command will reinstall nautilus, but you will lose your custom settings.

more here

[http://www.google.com/search?q=how+to+reinstall+nautilus+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=how+to+reinstall+nautilus+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by screaminfakah on 2009-11-24
you should never sudo nautilus
use gksu for anything working from a gui

---

### Post by mechro on 2009-11-24
Unset Key for trash_icon_name in Configuration Editor. Log out, Log in.

---

### Post by fancypiper on 2009-11-24
I believe you can restore the defaults by deleting /home/<user>/.gconf/apps/nautilus

---

### Post by Irony on 2009-11-24
Perhaps try deleting first;

```
/home/username/.gconf/apps/nautilus
```

Then reboot.

Just noticed that is what fancypiper said...

---

### Post by thedoommaker on 2009-11-26
thank you guys for your consideration and suggestions
but apparently none of them worked for me
or I've missed something 
but anyways I was so frustrated that I did a fresh install of ubuntu

---

