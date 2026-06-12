---
title: "Ubuntu Software Center crashes"
date: 2009-12-02
forum: General Help
---

### Post by horseradish on 2009-12-02
Hello,

My software center function worked ok but now it crashes within 2 seconds of appearing. It seems to load then vanish. I have also noticed soundconverter does the same now. Could it be a conflict with kdenlive ? I tried this recently. 

I am using the latest official Ubuntu (Koala ?)

Any ideas ?

---

### Post by endBc on 2009-12-02
Launch it from the terminal and let us know the output.

```
gksudo software-center
```

---

### Post by horseradish on 2009-12-02
> **endBc said:**
> Launch it from the terminal and let us know the output.

```
gksudo software-center
```

the same problem. There sems to be something interfering during loading. i can see by the stalling of the 'load' icon. Most programs can overcome it.

---

### Post by horseradish on 2009-12-02
> **horseradish said:**
> the same problem. There sems to be something interfering during loading. i can see by the stalling of the 'load' icon. Most programs can overcome it.

The only thing I can think of that I newly ran that might cause it is kdenlive. This asked me to set settings etc on its first run. 

Programs that won't load :
Brasero
Soundconverter
Soundrecorder
Movieplayer

Programs that load :
Avidmux
VLC player
Firefox

---

### Post by endBc on 2009-12-02
Launching it from the Terminal wasn't supposed to be a fix - we need it because there might be something that could help us solve this problem. Please do as I said - launch it from the Terminal and copy/paste the output here ( use [code] tags ).

---

### Post by horseradish on 2009-12-02
> **endBc said:**
> Launching it from the Terminal wasn't supposed to be a fix - we need it because there might be something that could help us solve this problem. Please do as I said - launch it from the Terminal and copy/paste the output here ( use [code] tags ).

"Could not initialize GStreamer: Error re-scanning registry , child terminated by signal"

---

### Post by horseradish on 2009-12-02
> **horseradish said:**
> "Could not initialize GStreamer: Error re-scanning registry , child terminated by signal"

anyone ? it seems to be a gstreamer issue

---

### Post by horseradish on 2009-12-02
still not ficed the problem. My guess is that kdenlive changed my gstreamer settings in some way. Any advice is welcome

the error is :

(software-center:3052): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:3052): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:3052): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:3052): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:3052): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:3052): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:3052): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:3052): GStreamer-WARNING **: adding type gint multiple times

(software-center:3052): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:3052): GStreamer-WARNING **: adding type glong multiple times

(software-center:3052): GStreamer-WARNING **: adding type guint multiple times

(software-center:3052): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:3052): GStreamer-WARNING **: adding type gulong multiple times
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by horseradish on 2009-12-02
Anyone ? I figure this may turn out to be a common bug. I have seen a few similar with songbird, and others saying the same happened after trying a video editor. My gstreamer programs are currently useless, including the software center

---

### Post by horseradish on 2009-12-03
problem solved

```
sudo apt-get remove frei0r-plugins
```

[http://ubuntuforums.org/showpost.php?p=8377817&postcount=8](http://ubuntuforums.org/showpost.php?p=8377817&postcount=8)

---

### Post by GulleyJimson on 2009-12-03
I am very new to ubuntu, but I am also having the same problem: when I launch the software center, the icon appears on the bottom of the screen, but the window never loads.  when I tried the above command from terminal, it went like this:   gksudo software-center     import pygtk   ImportError: No module named pygtk      any help?

---

### Post by Meanderer on 2009-12-05
Thank you horseradish!!!!! That fixed my week long problem too!!!! I couldn't find help anywhere here.

This certainly repaired and got back all my Apps requiring Gstreamer

> sudo apt-get remove frei0r-pluginsWhooohooo :D

---

### Post by arafatix on 2010-05-25
When i was writing the following code in terminal i found the following problem
root@ecds-open:~# gksudo software-center

(software-center:2385): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsttypefindfunctions.so': /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so: invalid ELF header

(software-center:2385): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstaudioresample.so': /usr/lib/gstreamer-0.10/libgstaudioresample.so: invalid ELF header

---

### Post by Baskey on 2010-06-08
HI am unable to run Software Centre tried this command gksudo software-center : 
and got the error below ... 

Traceback (most recent call last):  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 203, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 277, in _update_channel_list
    self.append(self.available_iter, [channel.get_channel_icon(),
AttributeError: 'list' object has no attribute 'get_channel_icon'

---

### Post by kavi99 on 2010-07-18
I had the same bug since 2 days, i did the following and it solved the problem
remove /var/cache/apt/*.bin

And see if that helps?

thanks to an old post from
[Michael  Vogt]("https://launchpad.net/%7Emvo")             wrote             on 2008-02-18:                          
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567)

---

### Post by benjiamobi on 2010-10-16
Errors were encountered while processing:
 usbmuxd
 libimobiledevice1
 upower
 gnome-session-bin
 gnome-session
 gnome-power-manager
 gdm
 gdm-guest-session
 gvfs-backends
 indicator-session
 libgpod4
 libgpod-common
 libimobiledevice0
 rhythmbox-plugins
 rtkit
 rhythmbox-ubuntuone-music-store
E: Sub-process /usr/bin/dpkg returned an error code (1)

why do i keep getting this errors whenever i install anything on my ubuntu, pls i need help on it because i think its preventing my ubuntu software center and main menu from opening, please any help will be appreciated, thanks

---

### Post by novus721 on 2010-11-25
> **kavi99 said:**
> I had the same bug since 2 days, i did the following and it solved the problem
remove /var/cache/apt/*.bin

And see if that helps?

thanks to an old post from
[Michael  Vogt]("https://launchpad.net/%7Emvo")             wrote             on 2008-02-18:                          
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567)

I just had the same issue and this fixed it, while other solutions listed above never worked due to a segmentation fault. Just remember to run it from sudo...

```
sudo rm -rf /var/cache/apt/*.bin

```

---

