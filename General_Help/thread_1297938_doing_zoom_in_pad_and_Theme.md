---
title: "doing zoom in pad and Theme"
date: 2009-10-22
forum: General Help
---

### Post by vitaly87 on 2009-10-22
hello !
i have an asus 1005ha and i want to da zoom with my pad what do i need to da that?
and i want to set up theme to remix ubuntu with what program i need to open that?
and what is 
**[Ubuntu GDM Theme]("http://www.ubuntu-art.org/?xcontentmode=8111")?**


thanks a lot

[B][URL="http://www.ubuntu-art.org/?xcontentmode=101"]
[/URL][/B]

---

### Post by duanedesign on 2009-10-22
GDM is the GNOME Display Manager, a graphical login program; Ubuntu and Xubuntu use GDM by default, Kubuntu, which uses KDM. Its the screen you see when you log in.

here is some info on making themes. For Gnome themes see the link: GTK themes.
[http://live.gnome.org/GnomeArt/Tutorials/](http://live.gnome.org/GnomeArt/Tutorials/)

---

### Post by duanedesign on 2009-10-22
Multi-touch support for touchpad

Open a Terminal (Applications > Accesories > Terminal) issue the following command. This creates a new document.

```
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi
```

copy and paste the following code into the new document.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
   <match key="info.capabilities" contains="input.touchpad">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">On</merge>
       <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
       <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.TapButton1" type="string">1</merge>
       <merge key="input.x11_options.TapButton2" type="string">3</merge>  <!--two finger tap -> middle clieck(3) -->
       <merge key="input.x11_options.TapButton3" type="string">2</merge>  <!--three finger tap -> right click(2). almost impossible to click -->
   </match>
 </device>
</deviceinfo>


```

Restart HAL and you are done.

```
sudo /etc/init.d/hal restart

```

You can test your laptop to see if it supports multi-touch. In a Terminal run:

```
synclient -m 100
```

The fifth column (f) is number of fingers on your touchpad. Place two or more fingers on the  touchpad. If you get a number two(2) then your computer supports multi-touch. If all you see is 1's and 0's in that column your hardware does not support this function.

---

### Post by vitaly87 on 2009-10-22
its wrote me only 0 or 1 . what can be done?

---

### Post by duanedesign on 2009-10-23
That means your touchpad is not detecting multiple fingers. It appears there is a [bug #308191]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191") reported and work is being done on this. Take a look at the bug and if you have any comments or information that has not been reported please comment on [the bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191").

---

