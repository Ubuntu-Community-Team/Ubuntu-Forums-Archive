---
title: "Screen capture programs?"
date: 2009-06-30
forum: General Help
---

### Post by Swerve1000 on 2009-06-30
Hello!

I was hoping for some recommendations for screen capture programs.

What I'd like to do is push Print Screen and be prompted to drag the mouse over the section of the screen that I'd like to capture and then save that area as a .jpg.

Is there anything like this for Ubuntu 9.04?

I'm making some newbie tutorials you see, and being able to select the areas would make things much easier.

Thanks for any help!

Appreciated :)

---

### Post by mbeach on 2009-06-30
I haven't used it, but have heard good things about:
[http://shutter-project.org/](http://shutter-project.org/)

---

### Post by credobyte on 2009-06-30
Hm, you can try scrot ( read man page for details on how to use it ) :) Tough, not sure about that "mouse" feature.

---

### Post by jmszr on 2009-06-30
Swerve1000,

+1 for Shutter.

---

### Post by mbeach on 2009-06-30
and if you are looking for help on the install:
[http://shutter-project.org/faq-help/ppa-installation-guide/](http://shutter-project.org/faq-help/ppa-installation-guide/)

and to get that default behaviour on printscreen
[http://shutter-project.org/faq-help/set-shutter-as-the-default-screenshot-tool/](http://shutter-project.org/faq-help/set-shutter-as-the-default-screenshot-tool/)

---

### Post by kaibob on 2009-06-30
The Imagemagick import utility will do what you want with the exception that it does not prompt you to drag/select the area to be copied (the cursor changes to indicate this). To test this, enter the following code in a terminal window and then drag/select a section of the screen. If this does what you want, then assign the command to the print-screen key or a panel launcher.

```
import -frame $(date +%m.%d.%y)-$(date +%H.%M.%S).jpg
```

BTW, you can use whatever file name that you like. I use the date and time to prevent previous screenshots from being overwritten.

---

### Post by mbeach on 2009-07-01
> **kaibob said:**
> The Imagemagick import utility will do what you want ...

```
import -frame $(date +%m.%d.%y)-$(date +%H.%M.%S).jpg
```


excellent tip - thank you.

---

