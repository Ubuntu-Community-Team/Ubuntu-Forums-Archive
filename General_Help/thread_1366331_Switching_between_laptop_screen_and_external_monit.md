---
title: "Switching between laptop screen and external monitor"
date: 2009-12-28
forum: General Help
---

### Post by solarmaze on 2009-12-28
I am as green as you can get when it comes to ubuntu or anything linux. I just installed ubuntu 9.1 on my Dell Latitude Laptop CPX. How do I swtich between the laptop screen and an external monitor. Under Windows XP I would use the keys Fn / F8 to toggle between both screens, one or the other. That apparently does not work with ubuntu. I need the simpleset methdo to do so.
Note: If I boot up with no external monitor connected, the laptop screen is working.
If I boot up with an external monitor connected, that monitor works, but no way to get back to the laptop screen without rebooting.
Thanks in advance for any help.
[EMAIL="bill@solarmaze.com"][/EMAIL]

---

### Post by audiomick on 2009-12-28
Hallo.
I know that one, but never figured it out. I think it is possible though.

It is not a good idea to post your email address. It is an invitation to put it on every spam list in the world...;) You should edit it out of your post. If anyone wants to write to you directly, they can do it with a personal message by clicking on your name.

---

### Post by Eyore15 on 2009-12-28
> **solarmaze said:**
> I am as green as you can get when it comes to ubuntu or anything linux.  I just installed ubuntu 9.1 on my Dell Latitude Laptop CPX.  How do I swtich between the laptop screen and an external monitor.  Under Windows XP I would use the keys Fn / F8 to toggle between both screens, one or the other.  That apparently does not work with ubuntu.  I need the simpleset methdo to do so.
Note: If I boot up with no external monitor connected, the laptop screen is working.
If I boot up with an external monitor connected, that monitor works, but no way to get back to the laptop screen without rebooting.
Thanks in advance for any help.
[EMAIL="bill@solarmaze.com"]bill@solarmaze.com[/EMAIL]

On my netbook it's "function" F3.

mcm

---

### Post by erlyrisa on 2009-12-28
It is possible to fix ... and on My eeepc the Fn keys worked out of the box on ubuntu.. but only becuase someone had made up a program for.

I think Ubuntu has matured since then (8.1) at I would have thought it would work.

(Iwish I could try it out on the PC I am typing to you on ... sadly this ones LCD inbuilt blew up last year so it's now just an Amiga style desktop pc)

--I did try the other FN keys, so far everything works including the touchpad lock - = sadly I don't want to do a Screen switch incase I can't get it back.

....other than the FN keys you can still do it in the display properties no? ie. System/preferences/display - pick the monitor and switch them both on, then switch the other off. (personally I would go for an extended diplay though- ie have both of them on, watch Utube on one and type away on the other)

---

### Post by junapp on 2009-12-28
it should be the fn + f8 looking at:
[http://commons.wikimedia.org/wiki/File:Dell_Latitude_CPx.jpg](http://commons.wikimedia.org/wiki/File:Dell_Latitude_CPx.jpg)

if not, try going into 
System -> Preferences -> Display

both your laptop and the external monitor should show up there, and you should be able to configure the resolution etc on each, or mirror the screens, depending on what you are attempting to do.

By 9.1, I'm assuming you mean 9.10.

---

### Post by chewearn on 2009-12-28
> **solarmaze said:**
> I am as green as you can get when it comes to ubuntu or anything linux.  I just installed ubuntu 9.1 on my Dell Latitude Laptop CPX.  How do I swtich between the laptop screen and an external monitor.  Under Windows XP I would use the keys Fn / F8 to toggle between both screens, one or the other.  That apparently does not work with ubuntu.  I need the simpleset methdo to do so.
Note: If I boot up with no external monitor connected, the laptop screen is working.
If I boot up with an external monitor connected, that monitor works, but no way to get back to the laptop screen without rebooting.
Thanks in advance for any help.

If you don't mind a few mouse clicks to achieve this, you should be able to switch displays using the Screen Resolution tool.  I think this can be found under: Menu > System > Preferences (not entirely sure where this is in latest Ubuntu).

However, if you really would like to activate the Fn+F8 key (if at all possible), command lines and editing of configuration files would be required.  This process would be complicated, and since I don't own this Dell laptop I can't help you directly.

But here are a short indication of what would be required:

1. Here is how to capture the keycodes:
[https://wiki.ubuntu.com/LaptopTesting/Keycodes](https://wiki.ubuntu.com/LaptopTesting/Keycodes)

2. The basic command for manipulating screen and resolution is xrandr.

```
xrandr --help
```Or:
```
man xrandr
```3. If the keypress execute acpi events, you might need to edit the appropriate configuration files under "/etc/acpi/events" so that the keypress would execute the required xrandr command.


BUT, I think it would be simpler to put the xrandr command into a script, which you could then add to the panel launcher.

---

### Post by solarmaze on 2009-12-28
Going to the display preferences is something I tried to do.  But I only see 1 monitor there... so I cannot "mirror" it, etc...  This is the case whether I boot up with the external monitor connected or not.

---

### Post by erlyrisa on 2009-12-28
> **solarmaze said:**
> Going to the display preferences is something I tried to do.  But I only see 1 monitor there... so I cannot "mirror" it, etc...  This is the case whether I boot up with the external monitor connected or not.


Oh ok ... this is still a slight problem with ubuntu (and linux in general)

...an initial install doesn't go through all the detection phases.

Thier is a fairly simple fix.

Change display resolution via an xrandr command ... after that all the capabilities of your computers display driver should show up in system/display.


here is an example command.

xrandr -v

choose one of resolutions and type something akin to

xrandr -s 1024x768

(I would pick the highest one though like 1280x1024 though.)


you see the gnu programmers decided a long time ago that it's not worth taking risks starting up a fresh installation in a resolution that may not work (windows up to XP did the same untill a driver is installed - linux is different in that the driver is already the closest mathc available upon first boot), the only exception to this rul is laptop screens where the risk is taken to boot in the highest resolution.



Anyway after running xrandr you should see the menu options

---

### Post by solarmaze on 2009-12-29
OK, here's how green I am...
How do I enter those commands... is there a command line window to open in ubuntu, like in Windows?
Thanks

---

### Post by cgb on 2009-12-29
yes, you can go to the Applications menu on the top bar and select Accessories and then terminal.

---

### Post by solarmaze on 2009-12-30
I set the resolution as instructed, but there is still only 1 monitor in the display preferences... even if I click detect monitors... so I cannot "turn them both on" or mirror.  This is the case if I boot without the external monitor cabled... in which case the laptop screen works.  Then if I cable the external monitor and do the command... same thing, and no change in the preferences.  If I boot with the monitored cabled, then only the external monitor has a display... then I enter the resolution command; then check the preferences... but once again, only 1 monitor shows up... even after a "detect."
At this point my only way to change monitors is to connect / disconnect the external cable and reboot!
What now?
Thanks in advance.

---

### Post by solarmaze on 2010-01-01
I heard that using FN / F8 to toggle between the laptop screen vs and external VGA connection was now supported in ubuntu... but apparently not.
I've got to believe that some sort of easy toggle has been implemented???

---

### Post by onyxwolf on 2010-01-13
I found this at [http://solnyshok.blogspot.com/2009/11/switch-between-laptop-lcd-and-external.html]("http://solnyshok.blogspot.com/2009/11/switch-between-laptop-lcd-and-external.html")
Hopefully it helps. I understand that the functions of Windows are more convenient "Out of the Box", but in the end they are going to be exactly the same; whereas, Ubuntu may take a little tweaking to get the same functionality, but with that tweaking you can easily, and completely, surpass the windows ability. 

$ xrandr

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192

VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm

   1280x1024      60.0*+   75.0 

   1152x864       75.0 

   1024x768       75.1     70.1     60.0 

   832x624        74.6 

   800x600        72.2     75.0     60.3     56.2 

   640x480        72.8     75.0     66.7     60.0 

   720x400        70.1 

LVDS1 connected (normal left inverted right x axis y axis)

   1280x800       60.0 +

   1024x768       85.0     75.0     70.1     60.0 

   832x624        74.6 

   800x600        85.1     72.2     75.0     60.3     56.2 

   640x480        85.0     72.8     75.0     59.9 

   720x400        85.0 

   640x400        85.1 

   640x350        85.1 

HDMI1 disconnected (normal left inverted right x axis y axis)

DP1 disconnected (normal left inverted right x axis y axis)

DP2 disconnected (normal left inverted right x axis y axis)


NOW go to System/Preferences/Keyboard shortcuts and add

WIN+F5 use only laptop LCD (fn F8 maybe!?!)

xrandr --output VGA1 --off --output LVDS1 --auto

WIN+F6 use only external monitor

xrandr --output LVDS1 --off --output VGA1 --auto

WIN+F7 use both (laptop on the left)

xrandr --output LVDS1 --auto --left-of VGA1 --auto

WIN+F8 use both (laptop above)

xrandr --output LVDS1 --auto --above VGA1 --auto

---

### Post by onyxwolf on 2010-01-13
If someone knows how to get xrandr to output whether or not the connected monitor is on or off you could grep it and make a pretty simple if/then bash script to have a keyboard shortcut call as a switcher. If output = LVDS1=off then xrandr --output VGA1 --off --output LVDS1 --auto.

Anyone know how to get xrandr to output which displays are on and off (not just connected/disconnected), so we can grep and script it?

---

### Post by chewearn on 2010-01-13
Yes, it's unfortunate that Ubuntu don't always work plug'n play like Windows.  In case of Windows, it's the computer manufacturers themselves which make it seamless, but Ubuntu is not in their world view.

Fortunately with some effort, Ubuntu is a lot more flexible.  And it's almost always possible to get Ubuntu to do what you want.  For instance, a while back I have to hack my eeePC to make dual screens and the Fn button works.

How I get switching of single and dual screens in Hardy:
[http://blog.chewearn.com/2008/09/22/eeepc-dual-screens-part-1/](http://blog.chewearn.com/2008/09/22/eeepc-dual-screens-part-1/)
[http://blog.chewearn.com/2008/09/23/eeepc-dual-screens-part-2/](http://blog.chewearn.com/2008/09/23/eeepc-dual-screens-part-2/)

How I get Fn keys working in Intrepid:
[http://blog.chewearn.com/2008/10/22/ubuntu-intrepid-ibex-on-eeepc-900/](http://blog.chewearn.com/2008/10/22/ubuntu-intrepid-ibex-on-eeepc-900/)

---

### Post by onyxwolf on 2010-01-13
I really like your set up page. A one stop to get the EEEPC 900 running great with Intriped. Maybe those scripts will work, but how does the fn key know to call those scripts? Anyways, good reiteration on my point.

---

### Post by chewearn on 2010-01-13
This page provide an overview:
[https://wiki.ubuntu.com/Hotkeys/Architecture](https://wiki.ubuntu.com/Hotkeys/Architecture)

Here is for help on debugging:
[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

An older page, which helped me previously:
[https://help.ubuntu.com/community/LaptopSpecialKeys](https://help.ubuntu.com/community/LaptopSpecialKeys)

---

