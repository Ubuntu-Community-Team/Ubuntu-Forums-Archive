---
title: "HOWTO: ubuntu on a tablet"
date: 2012-03-25
forum: General Help
---

### Post by David López on 2012-03-25
Hi.  I've been using ubuntu in my PC since 8.10 (please forgive my English mistakes, I'm Spanish). Recently I got a tablet,  I've installed ubuntu (oneiric) on it and I've applied a lot of tweaks  to make it friendly. Now I can use my tablet in a similar way to my PC. I'm far  from being an expert in ubuntu or tablets, but I wish that my experience  can help you. 

  The changes I've made:

[LIST=1]
[*] A **keyboard** that automatically hides/unhides in text boxes
[*] A **panel** with big icons
[*] Fill the **desktop** with applications
[*] Big **icons** that open with a single tap
[*] Increase text **fonts**
[*]**Window** decoration adapted to touchscreen
[*] Free space in the **indicators** bar
[*] A thick **scrollbar**
[*]Two finger **gestures** (zoom, scroll,...)
[*] Screen **rotation** to read books
[*] Configure the **button** of my tablet
[*] **software** for ubuntu and tablets
[/LIST]
Some picures (click on the links to increase):

[IMG]http://2.bp.blogspot.com/-MI3Spp2E_bo/T25b4wQMyNI/AAAAAAAAAKc/P6LCGLTzWfE/s320/Pantallazo+del+2012-03-25+00:41:06.png[/IMG]
[Big icons, large fonts, free space in the indicators bar]("http://2.bp.blogspot.com/-MI3Spp2E_bo/T25b4wQMyNI/AAAAAAAAAKc/P6LCGLTzWfE/s1600/Pantallazo+del+2012-03-25+00:41:06.png")


[IMG]http://1.bp.blogspot.com/-VLBwhOzuDiE/T2xsOCC8AqI/AAAAAAAAAKM/rvFvB7l_edM/s320/Pantallazo+del+2012-03-23+13%253A25%253A12.png[/IMG]
[Desktop can rotate, thick scrollbar]("http://1.bp.blogspot.com/-VLBwhOzuDiE/T2xsOCC8AqI/AAAAAAAAAKM/rvFvB7l_edM/s1600/Pantallazo+del+2012-03-23+13%253A25%253A12.png")

---

### Post by cariboo on 2012-04-23
A bump for the move.

---

### Post by David López on 2012-04-24
Oooops, I wanted to write each point in a different mesagge just like in the Spanish forum: [http://www.ubuntu-es.org/node/166530](http://www.ubuntu-es.org/node/166530), after writing the intro message I've never found it (I think I post in the **tutorial section**, IMHO that's the right section). I'll try the 12 points in a single long message, if you prefer reading step by step with a lot of images (I think this forum only allows 8 images per post) take a look at [http://ubuntutablet.blogspot.com](http://ubuntutablet.blogspot.com) 

Here I go...


**[SIZE=4]1 - KEYWORD[/SIZE]**

 Select **Typing Assistant** in **System Settings-Universal Access-Typing**  to start onboard 0.96 with your ubuntu session. onboard 0.97 is much  better, it automatically unhides when clicling on text boxes, terminal,  editors... and hides in other circunstances.

onboard 0.97 is included on ubuntu 12.04. To install it on ubuntu 11.10 add **ppa:onboard/snapshots**. Type in a terminal

 [FONT=Georgia] [B]sudo add-apt-repository ppa:onboard/snapshots
sudo apt-get update
sudo apt-get install onboard[/B][/FONT]
 
and restart. Click a few seconds in **Move onboard** button (the cross above Abc) to lengthen onboard from a corner.

I selected **Autoshow when editing text** and **Force window to top**. 

Don't forget** Show when unlocking screen**, or disable the password locking in **System settings-Screen**.


**[SIZE=4]2 - PANEL[/SIZE]**

 Icons in the left panel are a bit small for a tablet. I installed **Ubuntu Tweak **from **ppa:tualatrix/ppa**
  [B]
sudo apt-add-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak [/B]
  
You can increase the icon size up to 64 pixel in **Tweaks-Unity settings**. I also tweak some other things, as launcher hide mode and Icon backlight.


[SIZE=4]**3 - DESKTOP**[/SIZE]

 It's time to fill the desktop with programs. You can drag and drop them  from unity dash, but in my case the dash is fullscreen (netbook) by  default, and I can't hit the window button on top left with my fingers.  To reduce the dash size I started **Ubuntu Tweak** and selected **Desktop** dash size in **Tweaks-Unity settings**. Now there's a small space in the dash to drag and drop icons to desktop. 
  
[CENTER][[IMG]http://2.bp.blogspot.com/-OZ-_X5CK2T0/T2tOs2cG4ZI/AAAAAAAAAAc/4CGOM3r2R5g/s320/Pantallazo+del+2012-03-17+23%253A38%253A44.png[/IMG]]("http://2.bp.blogspot.com/-OZ-_X5CK2T0/T2tOs2cG4ZI/AAAAAAAAAAc/4CGOM3r2R5g/s1600/Pantallazo+del+2012-03-17+23%253A38%253A44.png")
[/CENTER]
 
  **Home folder** or **Trash** icons can be added from **Desktop icon settings** in **Ubuntu Tweak**.

   In the desktop, click on the top bar to open **View**. There are two options to order your icons: **Organize Desktop by name** and **Keep aligned**.
[CENTER][CENTER]
[/CENTER]
[LEFT]
[SIZE=4]**4 - ICONS**[/SIZE]

Icons are two small, and double-click is not confortable in a touchscreen. Open nautilus properties, for example from your **Home folder** and select **Edit-Preferences** in the upper bar menu. I raised the zoom level in the** Icon view default** to **150%** and choosed **Single click** to open items in **Behaviour**.
[CENTER]
[LEFT]
[SIZE=4]**5 - FONTS**[/SIZE]

Text size in icons, bar, nautilus... is small for a tablet desktop. I increased to **1.5** the **Text scalling factor** in the **Fonts** of **Ubuntu Tweak**. [CENTER] 
[/CENTER]
  [CENTER][[IMG]http://1.bp.blogspot.com/-o5jsi7ByCPA/T2tPF0jF49I/AAAAAAAAABc/sxzDsZyIg3g/s320/Pantallazo+del+2012-03-18+19%253A39%253A27.png[/IMG]]("http://1.bp.blogspot.com/-o5jsi7ByCPA/T2tPF0jF49I/AAAAAAAAABc/sxzDsZyIg3g/s1600/Pantallazo+del+2012-03-18+19%253A39%253A27.png")
[LEFT]
[SIZE=4][B]
6 - WINDOWS[/B][/SIZE]

In the left part of the window  decoration can emerge up to 3 different buttons (close, minimize,  maximize). Those buttons are unuseful for finger tapping because they  are too close one from another. Open **Ubuntu Tweak** and select **Window manager settings**, and customize the titlebar: I've selected **Close** at the left of the **Title**, and **Menu** at the right side. Menu is a very useful button that allows minimize, maximize, resize, move the window to another workspace...
[CENTER]
[[IMG]http://1.bp.blogspot.com/-p602rNoeEME/T2tPIape7bI/AAAAAAAAABo/uXed1bNY8y8/s320/Pantallazo+del+2012-03-18+19%253A46%253A00.png[/IMG]]("http://1.bp.blogspot.com/-p602rNoeEME/T2tPIape7bI/AAAAAAAAABo/uXed1bNY8y8/s1600/Pantallazo+del+2012-03-18+19%253A46%253A00.png")
[/CENTER]
 

  Resize is a very useful option, but I've found one particular case with strange behavior: I resize **Terminal** to fit with **onboard**, but gnome-terminal always starts with the same size. In **Edit-Profile preferences** I personalize it to 96 colums and 16 lines.
[/LEFT]
[/CENTER]



[SIZE=4]**7 - INDICATORS**[/SIZE]

 I like weather and CPU usage indicators, but the top bar is short in my tablet, so I've removed user and bluetooth indicators.

  If you don't want to **Show user session**, open **Ubuntu Tweak** and disable it from **Session control**, and restart your session.

  To remove **bluetooth** you need show it as a **Startup application**. Edit
  
  **sudo gedit /etc/xdg/autostart/bluetooth-applet-unity.desktop **

 [CENTER][LEFT] and change **NoDisplay** to **false**. Now open **Startup Applications** and unmark **Bluetooth**.
[/LEFT]
 
[/CENTER]
 Blue icon of **Universal access** can be disabled from **Universal access-Writing**. If you don't want **onboard** icon, unmark it from its own preferences.


[SIZE=4]** 8 - SCROLLBAR**[/SIZE]

Ubuntu has recently introduced a hidden scrollbar (**overlay scrollbar)**, beautiful but useful in touchscreens. I uninstall it, I will never miss it in my tablet.
[B]
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0[/B]

Restarting the session all windows have visible tiny scrollbars. I've increased length and width editing two files (**gtk-widgets.css** and **gtkrc**). You need to know the theme you are using, it is Ambiance by default. Then edit

**sudo gedit /usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css**
and change 2 parameters, **GtkScrollbar-min-slider-length: 80** and **GtkRange-slider-width: 25** (there are several GtkRange-slider-width, I've changed the one in **.scrollbar**). 

[CENTER][[IMG]http://1.bp.blogspot.com/-ewnzTSxA6kI/T2tQh4R3jmI/AAAAAAAAAGg/GiuH_dXLoMI/s320/Pantallazo+del+2012-03-21+10%253A26%253A16.png[/IMG]]("http://1.bp.blogspot.com/-ewnzTSxA6kI/T2tQh4R3jmI/AAAAAAAAAGg/GiuH_dXLoMI/s1600/Pantallazo+del+2012-03-21+10%253A26%253A16.png")
[/CENTER]

As gtk2 and qt scrollbars remain tiny, I edit

**sudo gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc**

and raise **GtkScrollbar::slider-width = 25** and **GtkScrollbar::min-slider-length = 80**. Now all the bars are thick, but gtk3 and gtk2 seem very different. Adding **GtkScrollbar::has-backward-stepper = 0** and **GtkScrollbar::has-forward-stepper = 0** to **gtkrc** the steppers dissapear and visual aspect is slighty better.  

[CENTER][[IMG]http://1.bp.blogspot.com/-GjjWHPZ9WJk/T2tPSYsUBnI/AAAAAAAAACs/ZMKEPef6epQ/s320/Pantallazo+del+2012-03-21+10%253A29%253A11.png[/IMG]]("http://1.bp.blogspot.com/-GjjWHPZ9WJk/T2tPSYsUBnI/AAAAAAAAACs/ZMKEPef6epQ/s1600/Pantallazo+del+2012-03-21+10%253A29%253A11.png")
[LEFT]

[SIZE=4]**9 - GESTURES**[/SIZE]

As a tablet user you probably want to  use finger gestures to scroll, zoom or rotate, and as a ubuntu user you  probably miss the right click. Maybe it is my failure but **utouch** package doesn't work for me, fortunately **twofing** does.

Download and uncompress twofing from [https://github.com/Plippo/twofing/downloads](https://github.com/Plippo/twofing/downloads) (at this moment Plippo-twofing-e84108b, 18th March 2012). You probably need some packages prior to compile **twofing**:
[B]
sudo apt-get install build-essential libx11-dev libxtst-dev libxi-dev x11proto-randr-dev libxrandr-dev[/B]

You need to find the ID of your touchscreen. I found mine with

**lsusb **

[CENTER][[IMG]http://3.bp.blogspot.com/-dzHy5jtGn8M/T2xRV4fAebI/AAAAAAAAAJU/GyS1fo0Emx0/s320/Pantallazo+del+2012-03-23+11:31:59.png[/IMG]]("http://3.bp.blogspot.com/-dzHy5jtGn8M/T2xRV4fAebI/AAAAAAAAAJU/GyS1fo0Emx0/s1600/Pantallazo+del+2012-03-23+11:31:59.png")

[/CENTER]
 In my case it is 72a1. I edited **70-touchscreen-egalax.rules** to change **ATTRS{idProduct}=="72a1"**. Compilation is now straightforward:
[B]
make
sudo make install[/B]

I added **/usr/bin/twofing** to **Startup applications** and  restart ubuntu to use two fingered gestures: scroll, zoom, rotate, right  click (tapping). Tapping and scroll work everywhere (even in desktop),  zoom and rotation in evince, eog,...

[CENTER] 
[/CENTER]
[SIZE=4]**10 - ROTATION **[/SIZE]

 Rotation is necesary to read books. Some programs as **fbreader** and **evince** has their own rotation buttons (**evince** is also compatible with the **twofing** rotation gesture).
  
  You can use **Monitors** to rotate desktop, but touchscreen stands  still (tapping in a corner is a mouse click in a different point). I've  made a launcher based on** rotatesceen.sh**. First of all you need the touchscreen id:[B] 

xinput list[/B]
[FONT=Georgia][CENTER][CENTER]
[[IMG]http://4.bp.blogspot.com/-i7iiTq9uQzw/T2xdLiIdVHI/AAAAAAAAAJc/ZAFWXMeSae8/s320/Pantallazo+del+2012-03-23+12:18:57.png[/IMG]]("http://4.bp.blogspot.com/-i7iiTq9uQzw/T2xdLiIdVHI/AAAAAAAAAJc/ZAFWXMeSae8/s1600/Pantallazo+del+2012-03-23+12:18:57.png")[/CENTER]
[/CENTER]
[/FONT]
9 [FONT=Georgia] in my case. Create a script 
[B]
sudo gedit /usr/local/bin/rotacion[/B][/FONT]
  
  with the contents
  
  *sudo bash /etc/acpi/rotatescreen.sh*
  *ROTATION=`cat /var/lib/acpi-support/screen-rotation`*
  *case "$ROTATION" in *
  *  right)*
  *  xinput set-prop 9 --type=float "Coordinate Transformation Matrix" 0 1 0 -1 0 1 0 0 1*
  *  ;;*
  *  *)*
  *  xinput set-prop 9 --type=float "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1*
  *  ;;*
  *esac*
  
  substituting both 9 with your id toudhscreen. Don't forget the execution permission:
 
 [FONT=Georgia] **sudo chmod +x /usr/local/bin/rotacion**[/FONT]
  
  To remove password type
  
 [FONT=Georgia] **sudo visudo**[/FONT]
  
and add the line 
  
  *david ALL=(ALL) NOPASSWD: /usr/local/bin/rotacion*
  
at the bottom of the file (obviously substitute david with your user name). Ctrl+X to save and quit **nano**.
 
Time to create the launcher: 
  
[FONT=Georgia]**sudo gedit /usr/share/applications/girar-escritorio.desktop**[/FONT]
  
with the data
  
  *[Desktop Entry]*
  *Name=Rotate screen*
  *Exec=sudo /usr/local/bin/rotacion*
  *Icon=system-restart*
  *Terminal=true*
  *Type=Application*
  
  Open the dash and search for this launcher. You can add it to the panel and desktop as usual.
  [CENTER]
[[IMG]http://1.bp.blogspot.com/-VLBwhOzuDiE/T2xsOCC8AqI/AAAAAAAAAKM/rvFvB7l_edM/s320/Pantallazo+del+2012-03-23+13%253A25%253A12.png[/IMG]]("http://1.bp.blogspot.com/-VLBwhOzuDiE/T2xsOCC8AqI/AAAAAAAAAKM/rvFvB7l_edM/s1600/Pantallazo+del+2012-03-23+13%253A25%253A12.png")


[LEFT][SIZE=4]**11 - BUTTON**[/SIZE]

 My tablet has a button. ubuntu recognizes it as a multimedia key (**Audio media**) that **Launchs media player**. I've changed to **Minimize window** from **Keyboard-Shortcuts**.
[CENTER] 

[LEFT][SIZE=4]**12 - SOFTWARE**[/SIZE]

 Some programs are specially usufel for tablets, starting with **onboard**. Read my first entry and update it to 0.97 version. Believe, you will not regret.
  
  **calibre** is a popular e-book format converter that can also be used to read them. However I prefer **fbreader** to read books: it works fine, **twofing** scroll is sweet and tapping passes the page.
  
  **easystroke** is an application to recognize mouse (one finger)  gestures. I've tested in my PC and I think it's great, but unfortunately  it doesn't work in my tablet, I must further investigate.
  
  I use **xournal** to grade student works, it's easy to highlight, frame, cross out... with one finger. **cellwriter** is a stylus writing recognizer. I don't use it, but I think it fits well with **xournal**.
  
  Your children enjoy **tuxpaint**, an application to draw with fingers.
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

