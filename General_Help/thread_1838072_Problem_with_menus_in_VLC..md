---
title: "Problem with menus in VLC."
date: 2011-09-02
forum: General Help
---

### Post by VisionaryVanGogh on 2011-09-02
Hi, I recently installed Natty on my computer. On of the first things I made sure to do was install everything necessary to run encrypted DVDs on my computer. Long story short, I was able to get encrypted DVDs to work on the Totem Movie Player, but now VLC is completely messed up. 

I can't navigate on the DVD menus properly, and whenever I play anything, I can't select the menu from the top. (so I can't change audio tracks, etc.) I've been searching, but haven't found any information on how to fix this problem. I have tried uninstalling VLC and reinstalling it, but the same problem occurs. I would really appreciate any help.

---

### Post by VisionaryVanGogh on 2011-09-04
Hey, I recently found out that people with Tablet drivers installed on their computers have also had problems with the menus on VLC. Would the fact that I have a tablet have something to do with my problem?
Also, the menus all work fine when before I play a file. As soon as I start playing, I can't select anything any more. (although the quick keys still work.) Also, I can't pause or skip around on the time line unless I get out of full screen mode.)

---

### Post by raja.genupula on 2011-09-04
[http://ubuntuforums.org/showthread.php?p=7181768](http://ubuntuforums.org/showthread.php?p=7181768)

---

### Post by VisionaryVanGogh on 2011-09-04
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?p=7181768](http://ubuntuforums.org/showthread.php?p=7181768)

Are you recommending that I post my problem in the multimedia forum, or is that an offer to the solution to my problem? Are you saying a fresh install is my only choice? 

My problem is different from the one described in that thread. Again, Totem DVD player works fine. But I find the quality of the video is weaker than in VLC. VLC plays the movies, and while the menus are broken, they kind of work. My main problem was the fact that the VLC menu bar, at the top of the screen won't work when playing a movie. (where is says _M_edia, _P_layback, _A_udio, etc.)

---

### Post by raja.genupula on 2011-09-05
give a try in two ways 

1. how shortcut keys are going 
2.tools-> preference -> reset to defaults . 

   hope you lose nothing by this operation .but i am not sure that its gonna solve your issue .just give a try . all the best

---

### Post by VisionaryVanGogh on 2011-09-05
> **raja.genupula said:**
> give a try in two ways 

1. how shortcut keys are going 
2.tools-> preference -> reset to defaults . 

   hope you lose nothing by this operation .but i am not sure that its gonna solve your issue .just give a try . all the best


So, yeah, the shortcut keys all work fine. And, I did try resetting the defaults, and it made no difference. But thanks for your help. And any more would be appreciated.

---

### Post by mc4man on 2011-09-05
maybe try disabling the globalmenu, either just in vlc or for all qt4 apps

To give it a little test first - open a terminal and run this
```
export QT_X11_NO_NATIVE_MENUBAR=1  && vlc
```

If that works out then vlc can be adjusted or just remove this package
appmenu-qt

---

### Post by VisionaryVanGogh on 2011-09-05
> **mc4man said:**
> maybe try disabling the globalmenu, either just in vlc or for all qt4 apps

To give it a little test first - open a terminal and run this
```
export QT_X11_NO_NATIVE_MENUBAR=1  && vlc
```

If that works out then vlc can be adjusted or just remove this package
appmenu-qt

Okay, so I put the code into the terminal that you suggested, and here's what happpened.

> zachary@zachary-System-Product-Name:~$ export QT_X11_NO_NATIVE_MENUBAR=1  && vlcVLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x1604120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1315415677)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4642): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")

Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[0x16f67f0] signals interface error: signal 17 overriden (0x7f46510d6450)
[0x16f67f0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x16f67f0] signals interface error: signal 17 overriden (0x7f46510d6450)
[0x16f67f0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
zachary@zachary-System-Product-Name:~$ 


EDIT: It made things worse. I am now having the problem with top menu bar in Totem now.

---

### Post by mc4man on 2011-09-05
> EDIT: It made things worse. I am now having the problem with top menu bar in Totem now.
An export only 'exists' in the terminal it was run from, no effect on totem or anything else.

Did vlc run or did it crash?
If you where to close that terminal, open a new one, - can you run vlc from a terminal w/ just a command of 
vlc

( the errors shown in your prior post - 
[0x16f67f0] signals interface error: signal 17 overriden (0x7f46510d6450)
[0x16f67f0] signals interface error: /usr/lib/libQtCore.so.4(?)[(nil)]
don't show up here but I've seen people post them, sometimes vlc doesn't run, other times it does.

---

### Post by VisionaryVanGogh on 2011-09-05
> **mc4man said:**
> An export only 'exists' in the terminal it was run from, no effect on totem or anything else.

Did vlc run or did it crash?
If you where to close that terminal, open a new one, - can you run vlc from a terminal w/ just a command of 
vlc

( the errors shown in your prior post - 
[0x16f67f0] signals interface error: signal 17 overriden (0x7f46510d6450)
[0x16f67f0] signals interface error: /usr/lib/libQtCore.so.4(?)[(nil)]
don't show up here but I've seen people post them, sometimes vlc doesn't run, other times it does.

When I type VLC into the terminal, the program runs as it did before. But I'm still having the same problems with the top menus, as I did before. Again, the media plays, but the top menu bar doesn't work properly. And since I entered in the suggested code, the top menu bar in Totem isn't working properly either. (the top menu bar works before I hit play, but once I start playing, I get problems)
EDIT: The top menu bar in totem works after I hit the pause button. Not the case with VLC.

Anyway, for further details, this is what happens when I type VLC in the terminal:
> zachary@zachary-System-Product-Name:~$ vlc
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x111f120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1315691224)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:5655): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[0x12117f0] signals interface error: signal 17 overriden (0x7fd78675b450)
[0x12117f0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]




---

### Post by mc4man on 2011-09-05
So  - to clear up 
When you opened vlc w/ the export, (which would have just returned vlc's 'menu's' to it's interface), vlc worked but the menus didn't ?
As seen in screen

---

### Post by VisionaryVanGogh on 2011-09-05
> **mc4man said:**
> So  - to clear up 
When you opened vlc w/ the export, (which would have just returned vlc's 'menu's' to it's interface), vlc worked but the menus didn't ?
As seen in screen

Yeah, basically, the menu at the top, where you click on _M_edia, _P_layback, _A_udio, etc. won't work when I play a video. When I click on the top menus, they kind of flash by for a second and disappear. But buttons on the bottom work, (play, pause, etc.) As do the quick keys. Its the menus at the top that won't work when playing media. (but they work when VLC isn't playing anything.

---

### Post by mc4man on 2011-09-05
Then maybe this is a tablet issue, myself don't have one to test.

What I might try - AND _keeping vlc's menu's in the vlc interface_ instead of the global menu (top panel), either thru the 1 time export in a terminal, removing appmenu-qt or adjusting vlc.desktop

Install  qt4-qtconfig
```
sudo apt-get install qt4-qtconfig
```
open it
```
qtconfig
```
Change the default gui style to cleanlooks - see screen, then close  qtconfig saving the change on the way out

Try vlc again, preferably with it's menu's in it's interface

( if no change then if desired you can open qtconfig again and change back to "Desktop Settings (Default)

---

### Post by VisionaryVanGogh on 2011-09-05
> **mc4man said:**
> Then maybe this is a tablet issue, myself don't have one to test.

What I might try - AND _keeping vlc's menu's in the vlc interface_ instead of the global menu (top panel), either thru the 1 time export in a terminal, removing appmenu-qt or adjusting vlc.desktop

Install  qt4-qtconfig
```
sudo apt-get install qt4-qtconfig
```
open it
```
qtconfig
```
Change the default gui style to cleanlooks - see screen, then close  qtconfig saving the change on the way out

Try vlc again, preferably with it's menu's in it's interface

( if no change then if desired you can open qtconfig again and change back to "Desktop Settings (Default)

I'm sorry, I don't think I was clear enough, the menu bar at the top is always there, when playing my media, it's just that the boxes that drop down when you click on the menus at the top, those don't work. I should have explained that better.
EDIT: But just in case, I did follow your instructions, and it didn't make a difference either.

---

### Post by VisionaryVanGogh on 2011-09-16
Well, because I'm a new user, and I didn't have much to save on my computer, I tried a fresh install, and I still have problems with VLC, but the menus on Totem work fine now. I also found that Mplayer works well, but I'm a new user, and I'm a bit confused and couldn't figure out how to install the GUI. (it's a bit deceptive that my profile says I've been a member since 2009, I briefly had Ubuntu before, but I had a faulty graphics card, and couldn't enable any drivers, so next computer, I converted back to Windows for a while)

If anyone could still help me with VLC, it would be much appreciated. (oh, I can't load DVDs on a lot of other media players I tried installing)

---

### Post by mc4man on 2011-09-16
nm

---

### Post by VisionaryVanGogh on 2011-09-17
> **mc4man said:**
> nm

I see that the reason for you editing your post was because you thought I was using 11.10. Nope, I'm using 11.04. Oddly enough, VLC works fairly well in WINE, but, I can't upload srt. files when using it in WINE. Nor can I load DVDs. But, the menus drop down fine when playing media without glitching out.

---

### Post by VisionaryVanGogh on 2011-09-21
Hi, is there any more information I could provide? Let me know, 
thanks.

---

### Post by VisionaryVanGogh on 2011-10-18
Hi, I just thought I'd say that a while ago, I was able to fix my problem. I went back to using Ubuntu Classic (with effects) went into the CompizConfig Settings Manager, clicked on OpenGL, and unchecked Sync to VBlank. That solved my problem. 

On a side note, since the upgrade to 11.10, I switched over to Xubuntu. I don't like Unity.

---

