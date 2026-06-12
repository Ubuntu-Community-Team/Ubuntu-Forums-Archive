---
title: "That was short-lived fun--Unity disappeared and now I can't run anything"
date: 2011-10-13
forum: General Help
---

### Post by egkeat on 2011-10-13
I did a thing wrong, I suppose.

I went fishing around for screen savers and how to get change the mouse cursors, windows and such, went to dash and opened the old compiz, and without my touching anything, Ubuntu froze and then the entire Unity shell disappeared!

Very unhappy with this.

---

### Post by effenberg0x0 on 2011-10-13
Hey,

Press Ctrl+Alt+F1 to F6 to get to a VT (Console) and login at the console prompt.

unity --reset
sudo service lightdm restart


(Might take a few tries)

Regards,
Effenberg

---

### Post by zemadz on 2011-10-13
Welcome to the club. Meanwhile can you use Ubuntu 2D mode? Select that when logging in.

---

### Post by harlequin_ on 2011-10-13
> **effenberg0x0 said:**
> Hey,

Press Ctrl+Alt+F1 to F6 to get to a VT (Console) and login at the console prompt.

unity --reset
sudo service lightdm restart


(Might take a few tries)

Regards,
Effenberg

Hi

When I do ctrl+alt+f1 a full screen terminal windows shows up and it asks (I guess) for my username and pw

```
<username> login
```

I tried everything (username and password combinations) but seems not to work. Any ideas?

PS: When I login with Unity 2D after a reboot it seems to lauch Unity (normal) without a problem

---

### Post by effenberg0x0 on 2011-10-13
> **harlequin_ said:**
> Hi

When I do ctrl+alt+f1 a full screen terminal windows shows up and it asks (I guess) for my username and pw

```
<username> login
```

I tried everything (username and password combinations) but seems not to work. Any ideas?

PS: When I login with Unity 2D after a reboot it seems to lauch Unity (normal) without a problem

When you installed Ubuntu you were asked for a username and password. This are the ones you should use. This is your user in the system. You'll need this user/password many times, everyday, to do a lot of things on the system. Make sure the caps lock, numlock or other keys like that are not pressed as you try to enter your login password at the VT.

Regarads,
Effenberg

---

### Post by harlequin_ on 2011-10-13
> **effenberg0x0 said:**
> When you installed Ubuntu you were asked for a username and password. This are the ones you should use. This is your user in the system. You'll need this user/password many times, everyday, to do a lot of things on the system. Make sure the caps lock, numlock or other keys like that are not pressed as you try to enter your login password at the VT.

Regarads,
Effenberg


Hi,

I know that I have a username and password. I've been using ubuntu for 3 years now : ) (I upgraded from 11.04, not a fresh install) But when that screen is displayed and when I enter my username and password nothing happens, it just says that the login was incorrect (or something like that).

---

### Post by harlequin_ on 2011-10-13
Hi, sorry about the previous post. I think the reason I could not login was because of a keyboard-layout issue.

Now I entered my username and password and was able to enter the commands you proposed. When I did 

```

unity --reset

```

the process stopped after displaying "initializing session options...done"
So I had to control+c and use the second command in order to login again. Any ideas now? When I entered
```

sudo apt-get install unity

```

It says there's nothing to install or upgarde, the newest version of Unity is already installed

---

### Post by egkeat on 2011-10-13
> **zemadz said:**
> Welcome to the club. Meanwhile can you use Ubuntu 2D mode? Select that when logging in.

2D works. At least that's a start.

---

### Post by Musmanno on 2011-10-13
I had something similar happen during beta. I logged back in with 2D unity and went to system settings. Turned out that some of the settings had been unchecked for some reason. I checked the ones needed to get Unity going again and then logged. It worked after that.

At which point I installed Gnome 3 shell, but that's another thread :)

---

### Post by effenberg0x0 on 2011-10-13
@harlequin

Good, you're logged in at the VT.

```
sudo unity --reset &<press enter a couple times, till youre back at the prompt>
sudo lightdm restart
```If it says that theres no session running then you will use
```

sudo lightdm start

```
The screen will switch to lightdm. If it does not automatically, use **Ctrl+Alt+F7**
Try to login normally. If you still have no panel/launcher, go back to that same VT (**Ctrl+Alt+F1 to F6 **- The one you are already logged in)
```

DISPLAY=:0.0 /usr/bin/ccsm &
```<press enter a couple times, till youre back at the prompt>

**Ctrl+Alt+F7** again

Do you see CompizConfig-Settings-Manager WIndow on your session now?
If so, check if Ubuntu Unity Plugin, OpenGL and Composite are activated. If the Ubuntu Unity Plugin already is activated, deactivate, wait a little (like 5 seconds) and reactivate it. If it complains about conflicts in a couple popups, answer all questions with the middle button.

If the Panel/Launcher still does not appear, back to the VT and once again
```

** sudo lightdm restart**

```

You may also try:
```
DISPLAY=:0.0 compiz --replace &
``` (no sudo on this one, ok?)

---

### Post by egkeat on 2011-10-13
Ok, so now everything's back, with what I really wanted it the first place! I have a desktop with "Activities" in the upper left corner and time in the center. I swear, I don't even know what I did...

---

### Post by harlequin_ on 2011-10-13
This is getting weird.

When I do 

```

sudo unity --reset &
sudo lightdm restart

```I get back to lightdm. Now I have a top panel (still no launcher etc) that looks like Unity top panel, but with no indicators etc. Plus, when I focus desktop, I still have GNOME menus at the top panel. The weird thing is that I have Compiz Effects enabled!

when I try to get back to VT things get nasty. I can't get back the terminal view but all I haev is 2 black (noised with moving white dots) boxes on the top of my screen just around the firefox adress bar. They look like small, dynamic (white dots moving), broken terminal windows. When I do Ctrl + tab they disappear, and then appear again. 

Another issue..
I am using 2 monitors (an external samsung monitor along with my laptop). When I shut down my computer and unplug the Samsung monitor and open Ubuntu, my laptop monitor only displays things it displays when my Samsung is plugged as well. So it (lenovo monitor) does not automatically become the primary monitor..

At this point I have no idea whether this thing originates from GNOME3, compiz, Nvidia settings or any other thing. I'm completely lost and I think I'll wait until a very efficient workaround or direct solution is revelaed.

Thank you a lot for your time!

> **effenberg0x0 said:**
> @harlequin

Good, you're logged in at the VT.

```
sudo unity --reset &<press enter a couple times, till youre back at the prompt>
sudo lightdm restart
```If it says that theres no session running then you will use
```

sudo lightdm start

```The screen will switch to lightdm. If it does not automatically, use **Ctrl+Alt+F7**
Try to login normally. If you still have no panel/launcher, go back to that same VT (**Ctrl+Alt+F1 to F6 **- The one you are already logged in)
```

DISPLAY=:0.0 /usr/bin/ccsm &
```<press enter a couple times, till youre back at the prompt>

**Ctrl+Alt+F7** again

Do you see CompizConfig-Settings-Manager WIndow on your session now?
If so, check if Ubuntu Unity Plugin, OpenGL and Composite are activated. If the Ubuntu Unity Plugin already is activated, deactivate, wait a little (like 5 seconds) and reactivate it. If it complains about conflicts in a couple popups, answer all questions with the middle button.

If the Panel/Launcher still does not appear, back to the VT and once again
```

** sudo lightdm restart**

```You may also try:
```
DISPLAY=:0.0 compiz --replace &
``` (no sudo on this one, ok?)

---

### Post by effenberg0x0 on 2011-10-13
If you have the panel, that's a start :) I'd say that if you manage to launch ccsm and activate Ubuntu Unity Plugin once more you may get a Launcher. The video glitches you mentioned are not very unusual when switching from GUI to VT and back, but certainly shouldn't be the way you mention. Ideally you should look your VGA model specifics for drivers, specific settings that might improve its compatibility, performance, reduce glitches, etc.

Regards,
Effenberg

---

### Post by harlequin_ on 2011-10-13
> **egkeat said:**
> I did a thing wrong, I suppose.

I went fishing around for screen savers and how to get change the mouse cursors, windows and such, went to dash and opened the old compiz, and without my touching anything, Ubuntu froze and then the entire Unity shell disappeared!

Very unhappy with this.

By the way, I should note that this exactly is how this issue started for me: Upgraded from 11.04 to 11.10, went to System Settings for configuring Compiz, could not find CompizConfigManagerSettings there, launched it from the dash, just clicked a few view buttons, and BAAAAM.

---

### Post by harlequin_ on 2011-10-14
Hi, 

Today I opened my Ubuntu again, (eventually) was faced the same look (no launcher and gnome menu at the top without any indicators etc) and said "whatever" and pressed alt+ctrl+t to try to launch a terminal window.

It launched the terminal window, then I opened ccsm and enabled Unity, and everything seems fine right now.. The only problem is that within ccsm when I click "Preferences" it seems to freeze for a while and (I'm not sure but) reset a few of my settings. But the biggest problem is solved.

Cheers

---

### Post by egkeat on 2011-10-14
Logging on in Ubuntu 2D worked for me. Once I went back out of that and logged back into Gnome 3, everything was fine....actually better than before.

---

