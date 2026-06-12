---
title: "numeric 10-keypad only working during login screen"
date: 2010-03-05
forum: General Help
---

### Post by sibble on 2010-03-05
I've tried several things, so bare with me here and I'll go through what I've done...


First I followed these instructions:
[http://ubuntuforums.org/showpost.php?p=5939996&postcount=5](http://ubuntuforums.org/showpost.php?p=5939996&postcount=5)
> Well incase anyone reads this months/years into the future and has the same problem, i've found a workaround.

First, install numlockx
sudo apt-get install numlockx

Then create a script to turn it on.
sudo gedit /etc/init.d/numlockon

Enter these two lines of code to your blank script. Save and close gedit.
#!/bin/bash
numlockx on

Make your script executable
sudo chmod +x /etc/init.d/numlockon

Then type this thing that does something that makes it work..
sudo update-rc.d /etc/init.d/numlockon defaults

Reboot and enjoy having a functioning numpad!


This didn't work for me, and when I tried to manually turn the service on using "sudo service numlockon on" I'd get an error saying "Error Opening Display!"


Next, I tested to see if it was actually starting or not:
[http://ubuntuforums.org/showpost.php?p=5123607&postcount=3](http://ubuntuforums.org/showpost.php?p=5123607&postcount=3)
> /usr/bin/numlockx && echo "SUCCESS" > /home/<yourname>/numlockx.log || echo "FAILED" >/home/<yourname>/numlockx.log
and I did get a "SUCCESS" in my numlockx.log


Finally, I went here:
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)
I added this code to /etc/gdm/Init/Default:
```
if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi
```
and rebooted.  When I was presented with the login screen, I attempted to use the 10-key numeric pad, and **IT WORKED**!

**However**, after I logged in, I tried using it again and it _stopped working_.


I have a feeling this should be an easy fix, as it still does work at the login screen, even if I log out.  It just doesn't work while I'm logged in.  Any help would be gratefully appreciated!



EDIT: For the sake of it, I'm using Logitech MX5500 Revolution.  I did want to leave that out as I figured it might have detoured some people from reading this thread ;)

---

### Post by dcstar on 2010-03-05
> **sibble said:**
> 
.........
EDIT: For the sake of it, I'm using Logitech MX5500 Revolution.  I did want to leave that out as I figured it might have detoured some people from reading this thread ;)

Numlock status is automatically saved when you log out of a session, if the key is not working after you log in then you have an incorrect keyboard setting or the key has been remapped.

There is no need whatsoever for that legacy numlockx stuff.

---

### Post by sibble on 2010-03-06
Well, I don't have a selection for my keyboard in the Keyboard Model list, so I'm not so sure what to pick there.  It definently didn't work out of the box, and I can see that a ton of people are having problems with my model - Logitech MX5500 Revolution.

I installed mx5000-tool and revoco, which control extra functions for the keyboard/mouse (respectively.)  However, those tools have nothing to do with the numlock.

The numlock key is actually a calculator button.

---

### Post by sibble on 2010-03-06
I guess what I'm going to do is uninstall numlockx, undo the edits I did to /etc/gdm/Init/Default and go through and test each Logitech model that is listed in the Keyboard Model list to see if one of those is at least similar to mine.

---

### Post by sibble on 2010-03-06
Ok, uninstalled numlockx and rebooted.  10-key still works at login (but not after login.)

Went through every keyboard model listed under Logitech and tested the 10-key, none of them work.  However, for now I'm going to keep "Logitech Generic Keyboard" selected, and I'm going to look through the Layout Options to see if there's anything I can much with.

---

### Post by sibble on 2010-03-06
This is the first time I've had a need to manually configure my mouse/keyboard in a while.  I read somewhere that configuration for this is done automatically now (by xorg I think?)

I want to manually configure my mouse/keyboard, because auto-configuration did not configure some things.

My 10-key numeric pad isn't working, my horiztonal (left/right) mouse wheel tilt isn't doing anything.  How do I map these things?

I did testing with 'xev' and I can see that it's seeing 10-key, and my mouse wheel tilts.

Can I edit xorg.conf and have those settings override any auto-configuration that is/was done?

---

### Post by dcstar on 2010-03-06
> **sibble said:**
> 
.........
EDIT: For the sake of it, I'm using Logitech MX5500 Revolution.  I did want to leave that out as I figured it might have detoured some people from reading this thread ;)

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/291269/comments/16](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/291269/comments/16)

As it describes, the Logitech Bluetooth USB adaptor is detected only as a "normal" keyboard/mouse adaptor by the simple X-screen login process - so you keypad works - but once you log into Gnome it recognises the adaptor as a fully functional Bluetooth Hub so that stops the keypad working.

Not a bug, just hardware that is too smart for its own (and the users) good.

---

### Post by sibble on 2010-03-07
Thanks for that, looks promising I will give it a try.
I'm usually good at searching, but I'm not surprised I didn't find this because there is a plethora of old information pertaining to "MX5500" and Ubuntu.

---

### Post by sibble on 2010-03-07
I connected another USB Keyboard/Mouse, also leaving the MX5500 dongle in.  Rebooted.  Logged in with the other USB Keyboard/Mouse, and no Bluetooth icon appeared in the notification area.

I also went to System-> Preferences -> Bluetooth and it stated that no Bluetooth adapter was available.

---

### Post by sibble on 2010-03-07
> **sibble said:**
> My 10-key numeric pad isn't working, my horiztonal (left/right) mouse wheel tilt isn't doing anything.  How do I map these things?

I made a mistake, horizontal scrolling (mouse button tilt left/right) works out of the box.

Still working on the 10-key though.

---

### Post by sibble on 2010-03-07
OK!

Almost every single key/button works.

To get the 10-key to work I followed this:
[http://forums.overclockers.com.au/showpost.php?p=9496565&postcount=2](http://forums.overclockers.com.au/showpost.php?p=9496565&postcount=2)
> Or you could stick this in ~/.xmodmap

 keycode 0x5A = 0
 keycode 0x57 = 1
 keycode 0x58 = 2
 keycode 0x59 = 3
 keycode 0x53 = 4
 keycode 0x54 = 5
 keycode 0x55 = 6
 keycode 0x4F = 7
 keycode 0x50 = 8
 keycode 0x51 = 9
 keycode 0x5B = period
 keycode 0x6C = Return
 keycode 0x56 = plus
 keycode 0x52 = minus
 keycode 0x3F = asterisk
 keycode 0x70 = slash
 keycode 0x4D =

and start each session with "xmodmap ~/.xmodmap" ...

This doesn't enable numlock but gives me the number keys; I hate Numlock being on because certain apps have behaved strangely in the past.

Text taken from ~/.xmodmap on the 486 running Gentoo 2007.

The only keys/buttons that don't work:
-Flip 3D Zoom/Window Manager
-Slash key (on numeric keypad)

Which aren't really that important to me anyway.  It would be cool if I could get the Window Manager and Zoom keys to work, but no big deal.  xev doesn't output anything when those keys are pressed.

Regardless, I'm happy!!

---

### Post by yniotis on 2010-05-18
Had the same issue with Lucid (with the mx5000 keyboard), fixed it going to system>preferences>keyboard on the tab "mouse keys" and unchecked the "pointer can be controlled using the keypad".

---

### Post by isleshocky77 on 2010-05-21
This was really bugging me, but it's on a system I don't always use so I hadn't looked for a solution until just now.  

Figured I'd let you know I was able to solve it by ticking the option for "Numeric keypad keys work as with Mac".  I don't have any other options checked off including the option for "Default num\eric keypad keys".

I have the Logitech MX5000 Keyboard set. Hope this helps someone and it's less work that inserting a startup script.

Some other notes:
* I have the keyboard layout set to "Logitech Generic Keyboard"
* Running Ubuntu 10.04 x32 (upgraded from Ubuntu 9.10 x32 [CLEAN INSTALL])
* Running on an old Compaq Presario V2335us
* Running it through bluetooth on the computer WITHOUT the supplied Logitech Bluetooth dongle.

---

### Post by saracen on 2010-05-24
> **isleshocky77 said:**
> 
Figured I'd let you know I was able to solve it by ticking the option for "Numeric keypad keys work as with Mac".  I don't have any other options checked off including the option for "Default num\eric keypad keys".


Yes this works!!!  Finally.  It also works with the supplied Bluetooth dongle because that is how I have it connected (Logitech MX 5000 here).

Just to be clear that option is under System -> Preferences -> Keyboard -> Layouts -> Options -> Miscellaneous compatibility options.

---

### Post by Automat2 on 2010-06-07
> **isleshocky77 said:**
> Figured I'd let you know I was able to solve it by ticking the option for "Numeric keypad keys work as with Mac". 

It works even with the Logitech Bluetooth dongle on. This is how I tried it too.

---

### Post by CausticVeritas on 2011-09-21
I finally figured out a fix for this, non of the other solutions worked  for me but this did.  So hopefully it will help someone else.  

1) Go to System > Preferences > Keyboard
2) Go to the Mouse Keys tab
3) Uncheck "Pointer can be controlled using the keypad"

The number pad should be functioning as expected now.

Cheers!

---

