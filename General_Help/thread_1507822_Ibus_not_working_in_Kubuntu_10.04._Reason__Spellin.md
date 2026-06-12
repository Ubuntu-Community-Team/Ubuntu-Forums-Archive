---
title: "Ibus not working in Kubuntu 10.04. Reason : Spelling Mistake"
date: 2010-06-12
forum: General Help
---

### Post by akshar_patel_47 on 2010-06-12
I've just installed kubuntu 10.04 and it's missing quite some stuff that was out of the box in its Gnome counterpart.

One such functionality is ibus. In Gnome, it works perfectly, however in kde not so much.

On giving the following command

```
im-switch -c
```

we can select the ibus-qt module. What the mistake here is that the command then looks for a package called

```
plasam-widget-kimpanel-backend-ibus
```

however, the real name of the widget is ```
"plasma-widget-kimpanel-backend-ibus"
``` which is already installed in Kubuntu

I think this is preventing Kubuntu users from using Ibus.

So if some senior Ubuntu people here can figure out any workaround please let me know as I'm using linux for my Desktop Publishing Business and I don't want to continuously switch between KDE and Gnome environments.

And if there's a replacement for ibus which can let me write Indian Languages mainly Gujarati in OpenOffice Applications please let me know.

Thanks in Advance.

---

### Post by Scrubru on 2010-06-25
It it a misspelling. Edit the content /etc/X11/xinit/xinput.d/ibus-kde:

```
kdesu kate /etc/X11/xinit/xinput.d/ibus-kde
```

Then kate props up and you can find the error at the last but second line:

```
DEPENDS="ibus, ibus-gtk, ibus-qt4, [COLOR="Red"]plasam-widget-kimpanel-backend-ibus[/COLOR]"
```

There we have it. Correct the misspelling.

---

