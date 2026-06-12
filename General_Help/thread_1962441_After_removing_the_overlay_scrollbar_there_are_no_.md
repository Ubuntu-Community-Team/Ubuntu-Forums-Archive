---
title: "After removing the overlay scrollbar there are no scrollbar buttons"
date: 2012-04-21
forum: General Help
---

### Post by hateregistering on 2012-04-21
I wanted to get back the old classic scroll bars in my terminal and removed the overlay scrollbar according to the following instruction

[http://www.itworld.com/software/214389/get-classic-scollbar-back-ubuntu-1110]("http://www.itworld.com/software/214389/get-classic-scollbar-back-ubuntu-1110")

Now I have got something close to what I want, but there are no scrollbar buttons that you can scroll one line at a time with. How can I get those buttons back?

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

---

### Post by sarang on 2012-05-01
From [http://askubuntu.com/a/81991](http://askubuntu.com/a/81991)

Just disabling or removing the overlay-scrollbars ... will get you back the scroll bars, but they will be missing the stepper buttons at the end of the bars because they have been disabled in the *Ambiance* theme. To re-enable them, put the following in the [FONT="Courier New"]~/.gtkrc-2.0[/FONT] file:
```

    style "default" {
      engine "murrine" {
        stepperstyle = 0
      }
    }
```

and the following in [FONT="Courier New"]~/.config/gtk-3.0/gtk.css[/FONT] file:

```
    .scrollbar {
      -GtkScrollbar-has-backward-stepper: 1;
      -GtkScrollbar-has-forward-stepper: 1;
    }
```
Usually, restarting the applications is enough for the changes to apply.

---

