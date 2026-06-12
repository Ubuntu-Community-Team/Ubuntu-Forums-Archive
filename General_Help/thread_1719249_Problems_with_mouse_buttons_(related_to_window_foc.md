---
title: "Problems with mouse buttons (related to window focus)"
date: 2011-04-01
forum: General Help
---

### Post by Jovik on 2011-04-01
Hi,

Today I found out that my Ubuntu has serious sporadic bug related to mouse/keyboard. It was quite of a surprise since I've been using Ubuntu 10.10 for 5 months now...

The problem is that when, for example, I use Opera web browser everything seems to be fine. But if I try to use Alt+Tab to change window or click anywhere but Opera window nothing happens! I have to unplug and replug my mouse to solve the problem.

I don't have this bug in the recovery mode and simple graphics. On other forums I found that people tested it with different environments (Gnome/KDE/etc) and problem remained. Some say it's X.org fault which registers button press but not button release event... ([Link]("https://bbs.archlinux.org/viewtopic.php?id=90973"))

Everything was fine until I ran updates in the morning.

Any help appreciated!

Cheers,
Jovik

---

### Post by Drengur on 2011-04-05
I have the same problem after installing 10.10. I've looked everywhere on the web and this problem seems quite common. I have tried a few fixes, some patches to x.org, disabling assistive technologies, disabling effects in compiz, installed XFCE4, etc. 

Nothing works.

I also found out that if you right click on the "active" window you can temporarily free your mouse and keyboard (this does not always work as some windows don't allow right-clicking).

10.4 was fine, so were all the editions before that. 

I am thinking about checking out the 11.4 beta. Otherwise I fear I have to switch distros. I have 3 other computers at my home running 10.10 with no problems, it's only my desktop machine that acts this way.

(I've tried different keyboards and mice, USB and PS/2)

---

### Post by Jovik on 2011-04-06
I've located the problem in my case. Apparently my mouse buttons wared-off (8 years old Logitech), which leads to sporadic short circuits. However, Mac OS X and Vista seem to handle issue much better. Now I'm using a new mouse and so far - no problems.

I found a thread with similar issue on one of the forums. It turns out this problem is above Linux distributions because it's related to X.org. Here is Google Translate of the thread: [Link]("http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=pl&tl=en&u=http%3A%2F%2Fforum.linux.pl%2Fviewtopic.php%3Fid%3D17388%26action%3Dnew&act=url"). You can try to edit your xorg.conf file.

---

### Post by Drengur on 2011-04-06
Thank you for this. Google Translate does a great job with Polish.

However this did not help. I changed my xorg.conf to look like this:

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
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse
        Option "CorePointer"
        Option "Device" "/dev/input/mouse0"
        Option "Protocol" "ExplorerPS/2"
        Option "ZAxisMapping" "4 5"
        Option "Emulate3Buttons" "true"
EndSection

Section "ServerLayout"
        Identifier "Main Layout"
        Screen 0 "Default Screen"
        InputDevice "Configured Mouse" "CorePointer"
EndSection
```

The problem persists.

I hope someone has further suggestions. Note that most of the threads regarding this problem are marked as solved, however no solution has worked for me so far.

---

### Post by Drengur on 2011-04-08
Disabling Compiz seems to work.

edit: It only worked until I rebooted.

---

### Post by supercolino on 2011-08-25
Same problem here on Ubuntu 11.04. I have disabled all Compiz plugins, but still no improvement.

Basically, the symptoms are that when I have the focus on a windows, I can't click on the icons and menus in the taskbar (clock, Applications, shortcuts, etc..). I don't know if it's a matter of time or number of clicks, but after click something like 15 times in 5 seconds, it works... but I lose the focus on the window and have to struggle to have it back.

Other strange thing. If I have for instance a console open (with focus) and Firefox, if I click on Google search field in FF, the caret displays in the field but if I type it goes to the console....http:Ah, and the keyboard works fine (typing, switch windows with  [http://http:](http://http:)

This bug is a naaasty one. I did nothing special recently, just updates (no idea what exactly) and updated VirtualBox, and that's about it. Some time ago I played with xorg.conf, but it had nothing to do with the mouse.

Ah, and the keyboard works fine (typing, switch windows with Win+D, etc.)

---

### Post by supercolino on 2011-08-25
While I was typing the message the selected text started to be pasted automatically when I left clicked and even doing nothing.... scary :( Under Windows I'd say my PC is infected...

---

### Post by drever on 2011-08-30
I have the similar problems as reported by colino since a week or so (Ubuntu 10.04 LTS). I cannot change the focus to other windows or use the menu. It's a strange bug and seems to occur without any pattern. Does anyone have an idea what it might be, or how to fix it?

---

