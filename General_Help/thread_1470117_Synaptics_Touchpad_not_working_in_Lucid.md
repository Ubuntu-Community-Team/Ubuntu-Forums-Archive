---
title: "Synaptics Touchpad not working in Lucid"
date: 2010-05-02
forum: General Help
---

### Post by mugetsu37 on 2010-05-02
Alright, I installed 10.04 on my HP dv6000 laptop two days ago; I had a couple of issues with the keyboard and the menus, but I fixed that. Now my Synaptics Touchpad isn't working. The weirdest part is that before I fixed the keyboard and menu problems the touchpad worked fine (except scrolling, I never tried it). I've been looking around, but everybody else's touchpad would work at some point in the process; mine wont work as soon as I start the computer. It is one of the touchpads that has the disable button, and that works fine.

Again, I am using an HP dv6000 laptop, all default hardware.

---

### Post by Flash__Gordon on 2010-05-02
I too have the same issue with a dv6000. Everything worked perfect in 9.10 (including remote control). 
 I have noticed that the touchpad will work prior to logging in. At the login screen I can move the mouse with touchpad. After I put in password and hit enter I can move mouse for a couple of seconds and then Boom, no function. USB wireless mouse works (good thing). Once I pressed Ctrl+Alt+F2, then Ctrl+alt+F7 and it worked until next reboot, but that has not since worked so not sure what the hell that was. (just coincidence I guess). 
 I boggles my mind how things that work flawlessly in previous version suddenly is broken in next. Shouldn't be happening, you'd think it was windoes for **** sake.

---

### Post by powerslave12r on 2010-05-03
Another frustrated dv6000 user here (amd x2 64bit). It was working like a charm for 3 days and now out of nowhere :
- Mouse moves around but clicks don't work.
 *and/or*
- Mouse stops responding after the login screen. 


Sucks I had to login to win7 to type this out. Looking for solutions. 

I'm having my doubts about:

- Flash  (in the Ubuntu-restricted-drivers)
- Gsynaptics
- Nvidia hardware drivers.

Any insight would be appreciated.




> **Flash__Gordon said:**
> ... I pressed Ctrl+Alt+F2, then Ctrl+alt+F7 and it worked until next reboot,...
EDIT: This works for me too.

---

### Post by vinaysetty on 2010-05-05
I am using HP Pavilion dv6000 too, my trackpad was working for a couple of days after installing Ubuntu 10.04, then suddenly it stopped working after my laptop went to sleep and woke up. Sometimes it works after rebooting, but freezes again after sometime. Its really frustrating as I always have to carry a mouse. Any help would be greatly appreciated.

---

### Post by afrodeity on 2010-05-06
[http://ubuntuforums.org/showthread.php?p=9248244#post9248244](http://ubuntuforums.org/showthread.php?p=9248244#post9248244)

---

### Post by bdk on 2010-05-07
> **powerslave12r said:**
> Another frustrated dv6000 user here (amd x2 64bit). It was working like a charm for 3 days and now out of nowhere :
- Mouse moves around but clicks don't work.
 *and/or*
- Mouse stops responding after the login screen. 


My exact same problems as well. I installed Lucid Lynx amd64 on my dv6000 a couple of days ago and it worked great. Yesterday I started to loose keyboard and mouse functionality.

My touch-pad and its buttons ONLY works on the login screen. After entering my password and pressing continue, my touch-pad immediately fails to respond. I have to use an external blue-tooth usb mouse.

My external mouse left click will eventually fail at the same time that my keyboard quits responding. I can still press 'CTRL+ALT+DELETE' to restart the computer. When my left click fails, it is as if the computer does not recognize that I've released the left mouse button.

There does seem to be some commonality with either dv6000 series or the synaptic touch pads going dead.

*-bdk*

---

### Post by dino99 on 2010-05-07
> **powerslave12r said:**
> Another frustrated dv6000 user here (amd x2 64bit). It was working like a charm for 3 days and now out of nowhere :
- Mouse moves around but clicks don't work.
 *and/or*
- Mouse stops responding after the login screen. 


Sucks I had to login to win7 to type this out. Looking for solutions. 

I'm having my doubts about:

- Flash  (in the Ubuntu-restricted-drivers)
- Gsynaptics
- Nvidia hardware drivers.

Any insight would be appreciated.





EDIT: This works for me too.

With X.org 7.4, you might rather consider to use gpointing-device-
settings, which is modern replacement for gsynaptics.

---

### Post by powerslave12r on 2010-05-07
I did something better. 

Installed Slackware 13.

---

### Post by bdk on 2010-05-07
Ok.. was able to fix my Synaptics issue via #42 on [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727). I tried #45 which is a short cut for #42 but that didn't work; most likely my fault.

Not sure if this will re-manifest itself with future updates but at least there is a bug report and a temp work around.

And in the typing of this up I decided to see if the touchpad on/off button worked which ended up locking my keyboard and could no longer click to select anything.

---

### Post by easteregg on 2010-05-07
It seems that touchpad on/off button is a dangerous one. I had this problem too. 

removed all of my gnome and metacity config files and it works fine now. price: lost all my configuration.

---

### Post by powerslave12r on 2010-05-08
I had it working with #42 and #45 too but the touchpad on off button reset the fix.

---

### Post by bford16 on 2010-05-08
Strangely, I had this problem with one account on my computer, but not the other.  Using the following command did work.```
gconftool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean true
```

---

### Post by wkpalan on 2010-05-10
The solution mentioned here worked for me, Even the on/off button works perfectly

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1451316](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1451316)

---

### Post by akila87 on 2010-06-26
This one fixed my touchpad.Even the on/off button works now.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727/comments/103](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727/comments/103)

---

### Post by onamattuphere on 2010-08-31
This worked for me.

Run:
```
gconf-editor
```

search for 'touchpad'

click on the first entry and click on the 'touchpad_enabled' checkbox twice.

---

### Post by amireldor on 2010-09-19
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

comment #93 this solved my problem (for now at least)
although i'm on hp dv6000

EDIT:
hmm looks like someone already showed the solution here :)
actually, I think i got the link from here
oh nevermind

---

### Post by npjoseph on 2010-10-01
I have the same problem with my HP tx1222au. The touchpad stops working if at all I use the touchpad disable button. This thread offers a fix: [http://ubuntuforums.org/showthread.php?t=1451316](http://ubuntuforums.org/showthread.php?t=1451316)

Hope this helps.

---

### Post by mas_sergio on 2010-10-29
> **lousygarua said:**
> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

comment #93 this solved my problem (for now at least)
although i'm on hp dv6000

EDIT:
hmm looks like someone already showed the solution here :)
actually, I think i got the link from here
oh nevermind


im going to try this. I have a DV6700 and I am having the same exact issue prior to login the mouse works fine at the username selection. Then after logging in nothing. Disabling the mouse and re-enabling it (via the button above the touch pad) somehow cuts off the keyboard from functioning as well. What is wrong with this? I think a recent update ruined my mouse/keyboard. After updating and putting my computer to sleep i ran into this problem. i don't know what's going on but I don't like it. im not purchasing a USB mouse either. PC w/o mouse is pretty much a brick. O.o

---

### Post by mas_sergio on 2010-10-31
> **mas_sergio said:**
> im going to try this. I have a DV6700 and I am having the same exact issue prior to login the mouse works fine at the username selection. Then after logging in nothing. Disabling the mouse and re-enabling it (via the button above the touch pad) somehow cuts off the keyboard from functioning as well. What is wrong with this? I think a recent update ruined my mouse/keyboard. After updating and putting my computer to sleep i ran into this problem. i don't know what's going on but I don't like it. im not purchasing a USB mouse either. PC w/o mouse is pretty much a brick. O.o

I'm back with great news... problem solved. To save people clicking and time here's the quick fix (you don't need another mouse nor usb mouse to fix keyboard will suffice).

Follow these instructions. I rebooted and my mouse works great! I have no idea what broke my mouse? possibly an update? O.o


I have a DV6700 Entertainment PC w/ synaptics touch pad. (nearly the same as the DV6000 and all other dv models for touchpad at least)

Note that when you disable the mouse via the button you have to press it several times (2 for me) to re-enable it. It was like that before it broke. I have no clue what broke this as I haven't altered my settings much. Anyhow onto the fix.

Print out these instructions or save them on your windows partition and then browse to it via ubuntu and open it with openoffice.org ALT F2 (windows keyboard duno abt a mac).

THIS FIXED MY PROBLEM AND NOW MY MOUSE WORKS GREAT AGAIN!
REMEMBER TO RESTART AFTER COMPLETION OF ALL INSTRUCTIONS. ENJOY!

):P=D>:biggrin:

> [B]Hi, I was having the same issue. I believe that the Synaptics touchpad driver and Gnome both disable the touchpad individually. For some reason, Gnome (in particular gnome-settings-daemon) fails to re-enable it; which is why you end up with a dead touchpad, once you disable it.
Here is what fixed it for me (HP Pavilion DV6730ec):
First of all, open a terminal. Press Alt+F1 to open the applications menu and choose the Terminal application from the accessories or use an external mouse to so.
To bring your touchpad back to life, enter the following command:
Code:
gconftool --type bool --set /desktop/gnome/peripherals/touchpad/touchpad_enabled true
The key "/desktop/gnome/peripherals/touchpad/touchpad_enabled" is where gnome-settings-daemon remembers that you disabled your touchpad. This is the reason, why it is disabled even after a reboot.
The issue will re-appear, next time you disable your touchpad. You need to prevent gnome-settings-daemon from disabling your touchpad in the first place, because the Synaptics touchpad driver does this already. To do so, run the following command in a terminal:
Code:
gconftool-2 --type string --set /apps/gnome_settings_daemon/keybindings/touchpad ""
This dissociates the key to lock your touchpad from gnome-settings-daemon. If for any reason, the latter command breaks the lock touchpad support for you, than you probably have a different issue. To re-associate the key with gnome-settings-daemon, run this command:
gconftool-2 --type string --set /apps/gnome_settings_daemon/keybindings/touchpad XF86TouchpadToggle
Hope this helps. I recommend rebooting after this procedure and check if this really fixed it for good. I noticed that the error only occurs only once after a reboot.
[/B]

---

