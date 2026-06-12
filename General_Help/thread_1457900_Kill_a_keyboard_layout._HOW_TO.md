---
title: "Kill a keyboard layout. HOW TO???"
date: 2010-04-19
forum: General Help
---

### Post by playcat on 2010-04-19
Hello everyone,

I installed Ubuntu 9.10 on my laptop, and opted to install serbian keyboard with serbian latin unice on it during installation.

As a result of that fortunate choice, I'm having that #$$!!""#$$ layout always, without being able to change it!!!

It appears during login time (gdm login) as default keyboard layout, it appears in any newly opened window and so on.

I tried to solve it by selecting serbian latin as default keyboard (notice: NO UNICODE), removing the damn unicode thing and then applying settings system wide, but with no success... On next reboot, my "dear" unicode appears again. I have that keyboard gadget next to clock icon on gnome, and it keeps showing SRB2, where "2" is in subscript, and represents that damn option :x

Could anyone PLEASE tell me where to find settings file(s) for that thing, to finally disable that thing for good? 

Thanks,
Dan

---

### Post by klemes on 2010-04-19
Run in a console or even better a tty:
```
sudo dpkg-reconfigure console-setup
```
and answer through the questions.
Also afterwards have a look in your /etc/X11/xorg.conf 
in your keyboard section if there is one and make sure you have opted for the correct keyboard layouts that you wan to use.

---

### Post by playcat on 2010-04-19
> **klemes said:**
> Run in a console or even better a tty:
```
sudo dpkg-reconfigure console-setup
```
and answer through the questions.
Also afterwards have a look in your /etc/X11/xorg.conf 
in your keyboard section if there is one and make sure you have opted for the correct keyboard layouts that you wan to use.

Thx for your reply... 

Unfortunately, this didn't help much... 

Here is the content of my xorg.conf file:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

```

Also, I think I did smt bad to my consoles, because they don't work any more :). Now they simply show something that looks like a bad attempt of going from graphics mode to text mode, with some buffers nto being cleared out, so I see something that looks like few windows zoomed in :shock:

---

### Post by klemes on 2010-04-19
I don't understand what could possibly go wrong in such a simple procedure.
Screen corruption from simply changing your keyboard layout?How the hell you achieved this???Anyhow did you rebooted the machine?
Because you have to reboot in order for the changes you made to take effect.
Try a reboot and tell us how it's going.
Also your xorg.conf has not a keyboard section so if you want to be able to change between us and serbian layouts you must add one such section.

---

### Post by playcat on 2010-04-19
> **klemes said:**
> I don't understand what could possibly go wrong in such a simple procedure.
Screen corruption from simply changing your keyboard layout?How the hell you achieved this???Anyhow did you rebooted the machine?
Because you have to reboot in order for the changes you made to take effect.
Try a reboot and tell us how it's going.
Also your xorg.conf has not a keyboard section so if you want to be able to change between us and serbian layouts you must add one such section.

Hey!

If nothing, I found out what was wrong with ttys ... Turned out I chose VGA font for tty, which wasn't such a good idea... 

My problem is maybe related to the fact that my keyboard isn't recognized (when checked from System->Preferences->Keyboard (tab: layouts)). I'm using HP 6735s notebook.

I need to check out how to add a keyboard section. I guess I can find some sample xorg.conf file aroung... Gotta run now, though... Working day is saying goodbye :)

Thx for your help... I'll follow up from home.

---

### Post by klemes on 2010-04-19
Wherever you will be asked at what type of keyboard you use you will choose PC(105) everywhere.That's all.
Here's my keyboard section:

```
Section "InputDevice"
        Identifier    "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,gr"
        Option          "XkbVariant"     ","
        Option          "XkbOptions"    "grp:alt_shift_toggle,grp_led:scroll"
EndSection
```

Just change gr with proper abbreviation for serbian language and you should be OK.


But if you choose correctly the keyboard layout the way I described in my first post you do not need a keyboard section in your xorg.conf.It isn't even taken into account in latest editions of Ubuntu unless you add the "AllowEmptyInput "off" option in your ServerLayout section.

Use Google for the above general information and ask here for what you do not understand or if you ran into trouble.

---

### Post by playcat on 2010-04-23
Hello,

I'm really grateful for your help, but it seems that my problem is a little more stubborn than that... 

I set my keyboard to PS(105) from tty with dpkg-reconfigure console-setup and everything went fine. However, even after few restarts, I still see that SRB2 as the default one.

I entered keyboard section to my xorg.conf, with us,sr and without sr (two times tried), still with no success :(

> **klemes said:**
> Wherever you will be asked at what type of keyboard you use you will choose PC(105) everywhere.That's all.
Here's my keyboard section:

```
Section "InputDevice"
        Identifier    "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,gr"
        Option          "XkbVariant"     ","
        Option          "XkbOptions"    "grp:alt_shift_toggle,grp_led:scroll"
EndSection
```

Just change gr with proper abbreviation for serbian language and you should be OK.


But if you choose correctly the keyboard layout the way I described in my first post you do not need a keyboard section in your xorg.conf.It isn't even taken into account in latest editions of Ubuntu unless you add the "AllowEmptyInput "off" option in your ServerLayout section.

Use Google for the above general information and ask here for what you do not understand or if you ran into trouble.

---

### Post by klemes on 2010-04-23
I am sorry maybe were looking in the wrong direction.If you are using gnome(ubuntu)go to System->Preferences->Keyboard and choose  the tab that says Layouts.See whichever layouts there are available there erase the one that you want to eliminate save and hopefully you will be all set.
Maybe have done this already ,just making sure we are OK from there.

---

### Post by playcat on 2010-04-23
Yes, I tried that before writing here :).

When I restert my computer, at login page, I can see two "keyboards", Latin Unicode and Latin... So, even though I'm applying my settings System wide, it doesn't have much success... 

I have just tried (as root) to grep all the files that have XkbLayout in them to see if there is one that still holds that setting thing.

---

### Post by playcat on 2010-05-18
Ok... I have 10.04 now, and this unicode layout appeared by itself!!!!!

I'm not sure what's going on... I don't remember if I formatted my partition though *blush* ... 

However, it's really frustrating!

Instead of Q, I keep getting this: &#456; (without any warning... this kb layout takes control of my laptop as it has a will of his own!)

What should I do?

---

### Post by playcat on 2010-05-18
> **playcat said:**
> Ok... I have 10.04 now, and this unicode layout appeared by itself!!!!!

I'm not sure what's going on... I don't remember if I formatted my partition though *blush* ... 

However, it's really frustrating!

Instead of Q, I keep getting this: &#456; (without any warning... this kb layout takes control of my laptop as it has a will of his own!)

What should I do?

Ok ... Seems like I got it going ... I can still see the damn serbian unicode layout, but at least default one seems to be ok... 

with some more work, i might even get to smt :)

---

