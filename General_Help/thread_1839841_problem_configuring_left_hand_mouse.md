---
title: "problem configuring left hand mouse"
date: 2011-09-06
forum: General Help
---

### Post by crazycactus on 2011-09-06
Hi, I just installed Lubuntu 11.04 and I need to configure the mouse for a left handed user.  I've tried going to the keyboard and mouse control panel in the preferences and selecting "left handed." However, when I do this, the control panel unexpectedly quits without saving the new setting.  I can't even click OK because the window disappears.

There must be a way to swap the left and right mouse buttons from a terminal session, but as a linux beginner, I do not know how to do this.

Can anyone show me how to do this?

Thanks.

---

### Post by TeoBigusGeekus on 2011-09-06
```
xinput -list
```
to list all input devices, in my case
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; ov519                                     id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=9    [slave  keyboard (3)]
```
The input device of interest is the ImPS/2 Generic Wheel Mouse (id=10).
So, find the autostart file of openbox and add this line into it
```
xinput set-button-map 10 3 2 1 4 5 &
```
Change 10 with your device of course.

---

### Post by crazycactus on 2011-09-07
Thanks, but I did what you said and it didn't work.  I found my autostart.sh file in: /etc/xdg/openbox/autostart.sh

I listed my devices
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=8	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard          	id=7	[slave  keyboard (3)]

```

so I saved ```
xinput set-button-map 8 3 2 1 4 5 &
``` at the top of the autostart.sh file and when I reboot, nothing changes. It is still a right handed mouse.

I did find the command: ```
xmodmap -e "pointer 3 2 1"
```
When I enter that as a regular line in the terminal, it works, but not when I save it as a line in the autostart.sh file.

Is the file i'm editing the right one, or is a different file or another autostart.sh in another location that i'm not seeing?

Thanks

---

### Post by TeoBigusGeekus on 2011-09-07
There should be an autostart file in your home folder.
Find it with this
```
find ~/ -iname "*autostart*"
```

---

### Post by crazycactus on 2011-09-07
I found an autostart folder in within my home folder but there is nothing in it.

This is what it looks like.
```
frank@frank-L800r:~/.config$ ls
autostart          gtk-2.0  lxsession   openbox         update-notifier   xpad
chromium           libfm    lxterminal  pcmanfm         user-dirs.dirs
gecko-mediaplayer  lxpanel  menus       Trolltech.conf  user-dirs.locale
```

I was thinking I could try to make a new autostart.sh with that xinput line.  Does the autostart.sh belong in the autostart folder or the openbox folder?

Thanks for the help.

---

### Post by TeoBigusGeekus on 2011-09-07
Put it in the openbox folder.

---

### Post by crazycactus on 2011-09-07
I tried making a new autostart.sh file with the pico editor. I saved it with that bit of code you suggested in the openbox folder and it still did not work. I then moved it to the autostart folder and that didn't work either.

I did notice that when I entered the xinput code in the regular terminal prompt, it worked. The only thing was when I switched my kvm switch to my other computer and then back to linux, the mouse went back to the right handed buttons.

the xmodmap code worked too, but was unaffected by the kvm switch, so I think that should be code to use.

I don't understand why it doesn't work in the autostart.sh file.  Maybe someone else has a suggestions on that.

Thanks for the effort though.

---

### Post by TeoBigusGeekus on 2011-09-07
Try to put it in a file called autostart (without the extension) in
```
~/.config/lxsession/Lubuntu/
```

---

### Post by crazycactus on 2011-09-09
I'll give that a try. There is no directory called Lubuntu in lxsession.  The closest thing is ```
~/.config/lxsession/LXDE
``` which has a file desktop.conf.

So I'll try putting the autostart file in there.

---

### Post by TeoBigusGeekus on 2011-09-09
Sorry for the constant experimentations, but I use solely openbox, not lxde - I'm also a lefty like you.
In pure openbox, the autostart file goes to ~/.config/openbox.
In lxde, though, opinion is divided...
See these:
[http://wiki.lxde.org/en/Autostart]("http://wiki.lxde.org/en/Autostart")
[http://wiki.lxde.org/en/LXSession]("http://wiki.lxde.org/en/LXSession")

---

### Post by crazycactus on 2011-09-09
Thats ok, I don't mind experiments.  Actually that last thing you told me to do worked.  I created the directory Lubuntu and put an autostart file in it. So I now have ```
~/.config/lxsession/Lubuntu/autostart
```

I tried several things at once and made a few different autostart and autostart.sh files in a couple of locations. Once it worked, I then narrowed it down to what you see above.

I'm actually a righty, but I had some pain in my right index finger at one point and switched to using my mouse left handed.  I noticed that having my mouse on the left edge of my desk freed up more space on the right or middle part of my desk for other objects, so I just kept it that way.

Thanks for the help and information.

---

### Post by TeoBigusGeekus on 2011-09-09
Aha! Brilliant!
I'm glad you've sorted it out.

---

