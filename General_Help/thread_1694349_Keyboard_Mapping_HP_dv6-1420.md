---
title: "Keyboard Mapping HP dv6-1420"
date: 2011-02-24
forum: General Help
---

### Post by Lamukra on 2011-02-24
Hi Guys!!!

I was searching internet for how to **bind** different **keys** in Ubuntu.

Main problems is that Space bar is not working and I need to bind it to another key like right Alt or Menu button.

Have read about **xkeycaps**, but on **HP dv6** there is a problem it does not recognize keyboard in right way, and there is no reaction if even though you bind the key with wrong keyboard recognition.

In Windows there is nice program, which can easily make this possible.

I am already frustrated with this issue and I am not a very experienced user in Ubuntu.

I cannot type a lot on HP laptop, because space is not working only copy paste. If somebody could help with this issue I would really be thankful.

In Ubuntu keyboard is set to **Generic 105-key(Intl)PC**
Layout is **US-international**

[B]HP Pavilion dv6-1420sq
[/B]
Thank you in advance!

---

### Post by Lamukra on 2011-02-27
anybody please help...

any advice???

---

### Post by Krytarik on 2011-02-27
I believe the simplest way to modify the keyboard mapping this is to follow this guide:
[https://wiki.edubuntu.org/Lkraider/XmodMap](https://wiki.edubuntu.org/Lkraider/XmodMap)

Though the "Ubuntu Community" officially recommends KeyTouch:
[https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)

---

### Post by Lamukra on 2011-05-03
> **Krytarik said:**
> I believe the simplest way to modify the keyboard mapping this is to follow this guide:
[https://wiki.edubuntu.org/Lkraider/XmodMap](https://wiki.edubuntu.org/Lkraider/XmodMap)

Though the "Ubuntu Community" officially recommends KeyTouch:
[https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)

Thank you! I will try it out, seems that it is the only ways to do the binding in Ubuntu, even better to buy a working keyboard

Appreciate you help!

---

### Post by Krytarik on 2011-05-03
Actually, I gathered some experience since then about remapping keys with "xmodmap".

I believe it's really the easiest way to use just that, not some fancy tool or whatsoever.

So, if you need some help with it, just say what key you would like to remap to Space, it should be very easy.

Greetings.

---

### Post by Lamukra on 2011-05-03
> **Krytarik said:**
> Actually, I gathered some experience since then about remapping keys with "xmodmap".

I believe it's really the easiest way to use just that, not some fancy tool or whatsoever.

So, if you need some help with it, just say what key you would like to remap to Space, it should be very easy.

Greetings.

I need to put space to "Menu" key - I believe it is called like that. The one just on the right from "Alt Gr"

Why this button - because it is not really used, normally it is the right click on the mouse - my girlfriend is not a keyboard geek, so for her will be enough of mouse's right click.

If it is complicated for "Menu" button the "Alt Gr" will be good to

I will continue my studies with xmodmap deeper then...

Thank you very much!!!

---

### Post by Krytarik on 2011-05-04
If it's not already there, create a file called ".Xmodmap" in your home directory with the following content:

~/.Xmodmap:```

keycode 135 = space
```The next time you login, you may be asked if you want to use those keymap file*, then just  choose "Add" and confirm with "OK". It should work then.

Greetings.

*depends on if you had such a file before, and did already confirm/disable those query

---

### Post by Lamukra on 2011-05-04
> **Krytarik said:**
> If it's not already there, create a file called ".Xmodmap" in your home directory with the following content:

~/.Xmodmap:```

keycode 135 = space
```The next time you login, you may be asked if you want to use those keymap file*, then just  choose "Add" and confirm with "OK". It should work then.

Greetings.

*depends on if you had such a file before, and did already confirm/disable those query

Krytarik, you are amazing :)... works perfectly and my girlfriend is happy as hell :) Thank you a Lot!!!

---

### Post by Krytarik on 2011-05-04
> **Lamukra said:**
> Krytarik, you are amazing :)... works perfectly and my girlfriend is happy as hell :) Thank you a Lot!!!
You're welcome! :)

---

