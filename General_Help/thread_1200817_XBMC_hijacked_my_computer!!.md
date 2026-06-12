---
title: "XBMC hijacked my computer!!"
date: 2009-06-30
forum: General Help
---

### Post by reydempto on 2009-06-30
So i was trying out different ways of networking my 360 to my computer. i have several hundred gigs of movies and stuff on my hard drive, and it looks a lot better on the 40 inch tv than on my crt monitor :)

i installed xbmc, and didn't like it, and finally settled with ushare.

problem is, when i restarted my computer, xbmc took over! no more ubuntu! so i logged out, and logged in as root into a terminal, and removed xbmc using apt-get. i removed all of its lib files as well. however, now when i restart, i get this error:

```
/etc/gdm/Xsession: Beginning Session Setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.exec: 1: xbmc: Not Found
(this is an error log from ~/.xsession-errors)
```

help me! i am using gnome's safe mode option to boot right now, but i need to get back to normal :(

---

### Post by K.Y.A on 2009-06-30
> **reydempto said:**
> So i was trying out different ways of networking my 360 to my computer. i have several hundred gigs of movies and stuff on my hard drive, and it looks a lot better on the 40 inch tv than on my crt monitor :)

i installed xbmc, and didn't like it, and finally settled with ushare.

problem is, when i restarted my computer, xbmc took over! no more ubuntu! so i logged out, and logged in as root into a terminal, and removed xbmc using apt-get. i removed all of its lib files as well. however, now when i restart, i get this error:

```
/etc/gdm/Xsession: Beginning Session Setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.exec: 1: xbmc: Not Found
(this is an error log from ~/.xsession-errors)
```help me! i am using gnome's safe mode option to boot right now, but i need to get back to normal :(


Simple. You installed XBMC live, which removes Ubuntu-desktop. You have to make sure you check what new packages will remove when you install them... simply run:

```
 sudo apt-get install ubuntu-desktop
```

---

### Post by reydempto on 2009-06-30
when i do that all i get is :


ubuntu-desktop is already the newest version.

---

### Post by K.Y.A on 2009-06-30
> **reydempto said:**
> when i do that all i get is :


ubuntu-desktop is already the newest version.

Hmm. try this:

```
sudo apt-get remove xbmc xbmc-live
```

---

### Post by reydempto on 2009-06-30
yeah, as i said, i already removed xbmc and all of its lib components. :)

---

### Post by K.Y.A on 2009-06-30
> **reydempto said:**
> yeah, as i said, i already removed xbmc and all of its lib components. :)

I was just hoping you forgot something. :)

What I think is going on is that you either removed an important lib or xbmc did not completely uninstall. Try this:


```
sudo apt-get remove --purge xbmc xbmc-live
```

and then

```
sudo apt-get clean
```

---

### Post by reydempto on 2009-06-30
when i enter the apt-get remove command, i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xbmc is not installed, so not removed
E: Couldn't find package xbmc-live

and when i apt-get clean, it just does its thing, and that's it.


EDIT: i re-logged, and i still get the same error as in my first post:

/etc/gdm/Xsession: Beginning Session Setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.exec: 1: xbmc: Not Found
(this is an error log from ~/.xsession-errors)

i know it's telling me what's wrong in that error, but i just don't know what it means lol

---

### Post by NightwishFan on 2009-06-30
Try fixing dependencies.

```
sudo apt-get update && sudo apt-get -f install
```

---

### Post by K.Y.A on 2009-06-30
haha, I see the solution! It's in the error!


```
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to** /etc/X11/xinit/xinput.d/default.exec: 1: xbmc: Not Found**
(this is an error log from ~/.xsession-errors)
```open a terminal, and run:

```
sudo gedit /etc/X11/xinit/xinput.d/default.exec
```Remove xbmc from the first line, and save it. Fixed. :p


**EDIT: If you cant get into Gnome, just run:**

```
sudo nano /etc/X11/xinit/xinput.d/default.exec
```

I hope you know how to use nano. After you remove xbmc from the first line press ctrl+X and then type Yes and hit enter twice.

---

### Post by reydempto on 2009-06-30
sudo gedit /etc/X11/xinit/xinput.d/default.exec opens a blank file :(
so i guess it doesn't exist. i found /etc/X11/xinit/xinput.d/*default*, but the term "xbmc" is not anywhere in the file.

also i tried fixing the dependencies, and nothing changes

---

### Post by reydempto on 2009-06-30
gosh i *really* don't wanna re-install ubuntu, because i have done so much to it since i upgraded...i super-duper don't feel like reinstalling compiz, emerald, ushare, and all the other stuff i've added in the past few weeks..

---

### Post by K.Y.A on 2009-06-30
> **reydempto said:**
> gosh i *really* don't wanna re-install ubuntu, because i have done so much to it since i upgraded...i super-duper don't feel like reinstalling compiz, emerald, ushare, and all the other stuff i've added in the past few weeks..

Don't worry, you can do it!! :lolflag:

---

### Post by K.Y.A on 2009-06-30
try this:

```
sudo gedit /etc/X11/xinit/xinput.d/all_ALL
```

---

### Post by reydempto on 2009-06-30
here's that file:
```

#
# This configuration provides default IM setting (user edittable)
# See im-switch(8) and /usr/share/doc/im-switch/README.Debian .

#
# Define IM for traditional X application with XIM
#
#  XIM server name used for XMODIFIERS="@im=$XIM"
#  XIM program /path/filename
#  XIM program command line arguments
#
#  These were traditional setting before uim and scim for CJK languages
#  Language   LC_CTYPE     XIM server XMODIFIERS              Start key
#  Japanese   ja_JP*       kinput2    "@im=kinput2"           Shift-Space
#  Korean     ko_KR*       ami        "@im=Ami"               Shift-Space
#  Chinese(T) zh_TW.Big5   xcin       "@im=xcin-zh_TW.big5"   Ctrl-Space
#  Chinese(S) zh_CN.GB2312 xcin       "@im=xcin-zh_CN.GB2312" Ctrl-Space
# 
XIM=
XIM_PROGRAM=
XIM_ARGS=
XIM_PROGRAM_XTRA=
# Set following variable to non-zero string if program set itself as deamon
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=
#
# Define GTK and QT IM module
#   They may or may not be using xim as the IM.
#
GTK_IM_MODULE=
QT_IM_MODULE=

#
# Define lists of packages neded for above IM to function
#
DEPENDS=

#
# Define X start up hook script to update IM environment
#

```

---

### Post by K.Y.A on 2009-06-30
> **reydempto said:**
> here's that file:
```

#
# This configuration provides default IM setting (user edittable)
# See im-switch(8) and /usr/share/doc/im-switch/README.Debian .

#
# Define IM for traditional X application with XIM
#
#  XIM server name used for XMODIFIERS="@im=$XIM"
#  XIM program /path/filename
#  XIM program command line arguments
#
#  These were traditional setting before uim and scim for CJK languages
#  Language   LC_CTYPE     XIM server XMODIFIERS              Start key
#  Japanese   ja_JP*       kinput2    "@im=kinput2"           Shift-Space
#  Korean     ko_KR*       ami        "@im=Ami"               Shift-Space
#  Chinese(T) zh_TW.Big5   xcin       "@im=xcin-zh_TW.big5"   Ctrl-Space
#  Chinese(S) zh_CN.GB2312 xcin       "@im=xcin-zh_CN.GB2312" Ctrl-Space
# 
XIM=
XIM_PROGRAM=
XIM_ARGS=
XIM_PROGRAM_XTRA=
# Set following variable to non-zero string if program set itself as deamon
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=
#
# Define GTK and QT IM module
#   They may or may not be using xim as the IM.
#
GTK_IM_MODULE=
QT_IM_MODULE=

#
# Define lists of packages neded for above IM to function
#
DEPENDS=

#
# Define X start up hook script to update IM environment
#

```

Very odd. There is nothing in that file either, go figure. :(

You could try this:

```
sudo apt-get remove gdm gnome
```

and then:

```
sudo apt-get install gdm gnome
```

and

```
sudo apt-get install xubuntu-desktop
```

If it asks, let xdm control the desktop. You can select your Gnome session if needed through the login screen.

---

### Post by reydempto on 2009-06-30
-.-

fail

i did all that, hit sudo reboot, and its still got the same error. 

XBMC I WILL FIND WHERE YOU LIVE AND I WILL FIGHT YOU.

---

### Post by K.Y.A on 2009-06-30
> **reydempto said:**
> -.-

fail

i did all that, hit sudo reboot, and its still got the same error. 

XBMC I WILL FIND WHERE YOU LIVE AND I WILL FIGHT YOU.

XBMX is not the problem :)

try this:

```
sudo dpkg-reconfigure xserver-xorg
```

Something like that.

I have good faith in that single command.

---

### Post by reydempto on 2009-06-30
well lets give it a whirl then.

---

### Post by K.Y.A on 2009-06-30
> **reydempto said:**
> well lets give it a whirl then.

Hopefully you didn't get the same error as in my signature there..

---

### Post by QIII on 2009-06-30
Funny.  I get

apt-get: error, **girl**friend-1.2 and **girl**friend-1.2-common, wife-1.1 already installed]

---

### Post by K.Y.A on 2009-06-30
> **QIII said:**
> Funny.  I get

apt-get: error, **girl**friend-1.2 and **girl**friend-1.2-common, wife-1.1 already installed]

Nice! That's outdated software though, wife-3.5 is already out. :D

---

### Post by NightwishFan on 2009-07-01
I get problems like this with Nvidia drivers sometimes. I was always forced to reinstall, though I am sure it is fixable..

---

### Post by .Maleficus. on 2009-07-01
Post the contents of your /etc/gdm/Xsession file.  If you have a .xsession in your user's directory, post that too.  And while you're at it, post the contents of /etc/X11/xinitc if you have one.

---

### Post by reydempto on 2009-07-01
well, that command you gave me made it so my computer wouldn't even boot ubuntu, so i went ahead and reinstalled it. i still haven't added a few things, but i'm pretty much back to where i was. no more xbmc lol

---

### Post by .Maleficus. on 2009-07-01
> **reydempto said:**
> well, that command you gave me made it so my computer wouldn't even boot ubuntu, so i went ahead and reinstalled it. i still haven't added a few things, but i'm pretty much back to where i was. no more xbmc lol
That's because the problem didn't lie within Xorg's configuration, it was GDM reading an init script and reading the line "exec xbmc" or something similar.

---

### Post by reydempto on 2009-07-04
its okay though, my ubuntu is running beautifully once more, thank christ i have a hard drive dedicated solely to my OS.

---

