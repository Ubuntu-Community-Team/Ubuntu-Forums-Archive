---
title: "Run C++ Application on Startup"
date: 2010-05-03
forum: General Help
---

### Post by thahir1986 on 2010-05-03
Hi friends,

I have ubuntu 8.04 now. I want to start the C++ simple Gui application before the login screen. Please help me whether i need to change the runlevel or i should write any shell scrips, if shell script means. HOw i write that?



Thanks

---

### Post by darolu on 2010-05-03
I don't think running an application before you log in is possible, other processes (like demons) do run before logging in but I don't think launching a GUI before logging in is possible; you can however prevent GDM from launching at start up if that's what you seek, just rename the gdm.conf file at /etc/init/ to something else (like gdm.conf-disabled):
```
$ sudo mv /etc/init/gdm.conf /etc/init/gdm.conf-disabled
```
This way you'll start at a terminal, where you will have to log in and then launch your application (starting X first may be necessary).

---

### Post by thahir1986 on 2010-06-16
i don' know whether it's a correct way or not. But i get it. :lolflag:

first we need to Stop the gdm manually and call the application using rc.local file in the home directory.

this is should be give after the 'start' call
> xinit #c++application
The application runs perfect.

But my problem is no window panel around my application and dialog box.
so i can't move the dialog pop up over my application.......


Please tell me any solution......:confused:

---

### Post by a-user on 2010-06-16
how about using autologin and then starting the app after login automatically?

---

### Post by thahir1986 on 2010-06-17
Thanks.

 But what i need, once we switch on the system it directly start the application and close the application leads to shutdown system...Others cant access anything in linux other than application(open file, edit, etc..thru application only).

can it possible in ur way?

---

### Post by a-user on 2010-06-17
uff, i understand. i know for sure this is possigle but sadly i don't remember how, nor where i saw a fitting howto.

did you already tried google?

---

### Post by thahir1986 on 2010-06-19
I can start the application before or after login page. But there is no window panel around the popup dialog box. so i can't move, close , resize the popup box..

I googled it...and nothing i did get!

---

### Post by thahir1986 on 2010-06-23
Now I find the way to start my application after the login page and also window panel around the pop up dialog which opens in my application and also i can disable the linux lxde menu panels and key board shortcut keys to avoid to open other things in linux.

Is any know how to create the custom splash screen for ubuntu ? I tried  the gsplashy but only blank screen was came ....anyone?!

---

### Post by a-user on 2010-06-23
how did you accomplished this?

---

### Post by thahir1986 on 2010-06-23
I done this in lxde.

For run the application after the login page:

we need to create a deskop file in /home/<user>/.config/autostart

if autostart folder not exist..create own. and within the autostart folder we need to create the .destop file...for example myapplication.desktop

```

[Desktop Entry]
Encoding = UTF-8
Name = MyApp
Icon = image.png
Terminal = False
Exec = /path/to/the/execution/file 
Type = Application
```save and exit.


To avoid the lxde menu panel :

```
#cd /etc/xdg/lxsession/LXDE/autostart
```within the file you can find 

```
@lxpanel -profile LXDE
```comment that line using '#' symbol and save...

To disable/enable the keyboard/mouse shortcuts:

Go to /home/<user>/.config/openbox/lxde-rc.xml

In this file u can disable/enable all the mouse and keyboard shortcut.  \\:D/

---

