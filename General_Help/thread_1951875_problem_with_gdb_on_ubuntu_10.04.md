---
title: "problem with gdb on ubuntu 10.04"
date: 2012-04-03
forum: General Help
---

### Post by saam6066 on 2012-04-03
Hi, I have ubuntu 10.04 on my PC and after installing CUDA 4.1 and Kate editor on it, everything seems to have some problem... when I want to open anything with gedit it shows as if it's trying to open it and nothing happens, the same thing happens when I want to open an image with image viewer or change the desktop's background..

there's also some problem with the applications on the upper and lower panel such as clock or show desktop and I cannot load them...

what do you think have caused these problems and how I can fix it? is it related to the CUDA or some other software that I've installed?

thanks in advance for any help.

---

### Post by flurospar on 2012-04-03
It looks like [segmentation fault]("https://en.wikipedia.org/wiki/Segmentation_fault").

To confirm this, just type the name of the app you want to start in the terminal (provided you can start the terminal). If not, boot into recovery mode and select the "Resume normal boot" option.

Here you can type the name of the app you want to start. If you see something like this when starting the app:
```

segmentation fault

```

it confirms that its a segmentation fault.

Its not related to any program that you installed.

As for the missing applets, have you tried:
```

sudo dpkg-reconfigure gnome-applets

```

---

### Post by saam6066 on 2012-04-03
> **flurospar said:**
> It looks like [segmentation fault]("https://en.wikipedia.org/wiki/Segmentation_fault").

To confirm this, just type the name of the app you want to start in the terminal (provided you can start the terminal). If not, boot into recovery mode and select the "Resume normal boot" option.

Here you can type the name of the app you want to start. If you see something like this when starting the app:
```

segmentation fault

```

it confirms that its a segmentation fault.

Its not related to any program that you installed.

As for the missing applets, have you tried:
```

sudo dpkg-reconfigure gnome-applets

```

Yes I get the segmentation fault when I try to run these programs, what should I do to fix it then? and for the missing applets yes I tried ```

sudo dpkg-reconfigure gnome-applets

``` but it's still the same :confused:

---

### Post by saam6066 on 2012-04-19
I think this problem happens when I install zlib which I've downloaded from it's website. does anyone have any idea what I can do to fix it?:-k

---

