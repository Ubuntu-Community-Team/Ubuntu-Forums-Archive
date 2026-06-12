---
title: "Almost there"
date: 2011-11-05
forum: General Help
---

### Post by Kermit524 on 2011-11-05
Hi,
Having upgraded my system to Oneiric, and setting it back to Gnome Classic - almost everything is OK, but 2 things. I have tried to look them up on Google prior to sending this post, but cannot find anything. Hope someone can help:
1. On Nautilus Window display - I miss the 'go up one level' button. I have only the 'back' 'forward' and 'search' buttons. Anyone came across such a behavior? 
2. Image viewer not working. If I get it right - the old Image Viewer is now called 'the Eye of Gnome'. But it just doesn't work for me. Anyone knows anything about this?
Many thanks in advance,
Michal

---

### Post by Kyoushuu on 2011-11-05
1. One of the changes in Nautilus 3.
2. Default GNOME Image Viewer is "Eye of GNOME", though it just says "GNOME Image Viewer". It's also the default in Ubuntu. If you have problems, try running "eog" in the terminal, it might show some error message. A Photo Manager, Shotwell, is also installed by default.

---

### Post by Kermit524 on 2011-11-06
Thanks Kyoushuu!
Re - 1: 'One of the changes in Nautilus 3' - Is there any work-around for this thing? I find it so weird they actually gave up this option in the window display- it makes no sense.
2. Thanks for the tip: I have ran eog on the terminal, and got "GLib-GIO-CRITICAL **: Timeout was reached" - so I googled it up and it is indedd a bug with the Glib library. They suggest to downgrade it to a 'stable release', only problem now is - I have no clue how this is done...

Many thanks again for your help,
Michal

---

### Post by coldraven on 2011-11-06
Try installing Sushi file previewer from the Sofware Center.
It is mentioned as item 5 in this article:
[http://www.omgubuntu.co.uk/2011/10/10-things-to-do-after-installing-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/10-things-to-do-after-installing-ubuntu-11-10/)

---

### Post by Kermit524 on 2011-11-06
> **coldraven said:**
> Try installing Sushi file previewer from the Sofware Center.
It is mentioned as item 5 in this article:
[http://www.omgubuntu.co.uk/2011/10/10-things-to-do-after-installing-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/10-things-to-do-after-installing-ubuntu-11-10/)

Thanks! In the meantime I have installed Shotwell, and after figuring out how to make all my images associate with it by default - all's good on this front.

(On the window display front - I am still amazed at the loss of the  'up one level' option. How come everybody else is so calm about this?... )

---

### Post by Kyoushuu on 2011-11-06
1. Use the breadcrumbs (the button above the tabs and to the left of the  arrows) to go up or down. You can go up multiple levels using this. You  may also go to the menu then Go -> Open Parent. You may also press  Alt+Up to do this. There's no workaround that I know that can bring it  back, since the breadcrumbs do the same functionality.

2. You may compile the stable release of GLib (which, on the time of  writing, is 2.30.1; check the last version with an even minor (second)  version number here: [http://ftp.gnome.org/pub/gnome/sources/glib/](http://ftp.gnome.org/pub/gnome/sources/glib/)) by opening a terminal then executing these:
```
cd
wget http://ftp.gnome.org/pub/gnome/sources/glib/2.30/glib-2.30.1.tar.xz
tar xJf glib-2.30.1.tar.xz
cd glib-2.30.1/
./configure
make
sudo make install
sudo make uninstall
sudo checkinstall --pkgname=glib --pkgversion=2.30.1 --default --fstrans=no --install --backup=no
```
I'm not sure if it will work. The above commands should install glib to /usr/local and should override the older library, though I'm not sure if it has bad effects to other programs.
[COLOR=DarkRed]**WARNING**[/COLOR]: GLib is a very important library of your system, I can't guarantee that doing this will not cause any problems. If there's a problem caused by this, or Ubuntu updated GLib to fix the problem (you may check if the bug is fixed by checking if this bug is mentioned in Update Manager's Changes tab, or if it is reported in Launchpad and the status is changed to "RESOLVED"), you may run ```
sudo apt-get remove glib
``` to remove it.

---

### Post by 3rdalbum on 2011-11-06
> **Kermit524 said:**
> Thanks Kyoushuu!
Re - 1: 'One of the changes in Nautilus 3' - Is there any work-around for this thing? I find it so weird they actually gave up this option in the window display- it makes no sense.

Apparently it's because people usually use Nautilus with the "breadcrumbs" view, and when you've got the breadcrumbs showing you don't need a "Go Up" button.

I usually use the "location" view instead of the breadcrumbs, but it only took a few days to get used to not having a Go Up button. Usually Go Back and Go Up are the same thing anyway, when you think about it.

---

### Post by Kermit524 on 2011-11-06
Thanks again, Kyoushuu - I will look it up. And 3rdalbum - Alt + arrow-up, is a good compromise. Thanks for the tip!

---

### Post by grahammechanical on 2011-11-06
As I use the file manager in Oneiric to drill down into my folder structure I notice that the path is put in the space to the left of the back and forward buttons.

I can go up the path by clicking on an earlier folder that has been opened. And I do not have to do it one click at a time as you would when clicking that UP arrow in earlier versions of the File Manager. With this feature you can go direct to a previous folder that you have come from.

This way might not be so good in your opinion but I think that it is better.

Regards.

---

### Post by Kermit524 on 2011-11-07
> **grahammechanical said:**
> As I use the file manager in Oneiric to drill down into my folder structure I notice that the path is put in the space to the left of the back and forward buttons.
Hi, thaks but I am not sure I get it. I tried to dbl click on the file path but didn't get anything...

---

