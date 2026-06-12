---
title: "dual monitors and &quot;dead space.&quot;  How do I get rid of it?"
date: 2012-02-06
forum: General Help
---

### Post by dorlow on 2012-02-06
Ok, I don't know how I did it on my last setup a few months back, but I can't get it to work the same.  I'm attaching a screenshot.  My laptop monitor sits a little bit lower than the screen to the right.  So, when I move my mouse to the screen on the right, I like the cursor to move straight and not jump.  The screen to the right physically is about 2 inches taller than the laptop screen.  So, if I move my mouse cursor to the left most of the right screen where I'm above the laptop, it should act like it's at the corner of the screen until I move the cursor down to the top of the laptop screen.  Then I should be able to move the mouse over.

Right now I can move the mouse around in the dead area.  If I don't put a bar across the top of my laptop screen and I sort my icons, they will go into the dead space.

I've been playing around with the absolute settings in nvidia and I can't get it to work.  Any ideas on how I need to change my xorg.conf file to work this way?

Also something else weird.  Everytime I make a change to my video, I get another blank bar going across the top of my laptop screen.  I can't get rid of them.  If I right click on them, I get nothing.

---

### Post by doobrie on 2012-02-07
I have a similar problem on my setup because my laptop and my monitor have different resolutions.

The fix is to grab the screen on the Displays settings option and just move it up or down.

Does that work?

---

### Post by dorlow on 2012-02-10
That doesn't work because my monitor that's my main monitor is lower physically than the big monitor.  If I were to do that, the cursor going from the left monitor to the right monitor would be way off... it would jump a ton.

---

### Post by dorlow on 2012-02-10
I just tried it again.  When I change it from TwinView to seperate X screens, it works OK until I reboot.  Then the screens line up right, but my computer takes forever to boot and none of the menus load.  I then have to restore my xorg.conf file to get back into x-windows.

---

### Post by pqwoerituytrueiwoq on 2012-02-10
using separate displays screws up compiz (try metacity) on the second monitor
i managed to get compiz working on both displayed bu i have not automated it
my thread
[http://ubuntuforums.org/showthread.php?t=1921352](http://ubuntuforums.org/showthread.php?t=1921352)

---

### Post by dorlow on 2012-02-10
I uninstalled compiz and made sure I logged in with no effects.  Then I switched back my xorg to separate x screens and still logged in with no effects and didn't help.  When I do that, some reason my computer logs in extremely slow and nothing will load on my main monitor.

---

### Post by pqwoerituytrueiwoq on 2012-02-10
unckeck the enable xrenia (i know i is spelled wrong) thingy
that thing makes it lag like hell but you will not be able to drag windows between the screens without is unless you use twin view

---

### Post by dorlow on 2012-02-10
So, I just read that other post a little closer... I get an error when I tried it...


```

david@davidorlow-pc:~$ sudo apt-get install xdotool
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-serialization1.46.1 libunity-misc4 indicator-power
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxdo2
The following NEW packages will be installed:
  libxdo2 xdotool
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.7 kB of archives.
After this operation, 270 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libxdo2 i386 1:2.20110530.1-3ubuntu1 [24.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xdotool i386 1:2.20110530.1-3ubuntu1 [41.0 kB]
Fetched 65.7 kB in 0s (69.4 kB/s)
Selecting previously deselected package libxdo2.
(Reading database ... 179512 files and directories currently installed.)
Unpacking libxdo2 (from .../libxdo2_1%3a2.20110530.1-3ubuntu1_i386.deb) ...
Selecting previously deselected package xdotool.
Unpacking xdotool (from .../xdotool_1%3a2.20110530.1-3ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libxdo2 (1:2.20110530.1-3ubuntu1) ...
Setting up xdotool (1:2.20110530.1-3ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
david@davidorlow-pc:~$ xdotool mousemove --screen 1280 800
Usage: mousemove [options] <x> <y>
-c, --clearmodifiers      - reset active modifiers (alt, etc) while typing
--screen SCREEN           - which screen to move on, default is current screen
--sync                    - only exit once the mouse has moved
-w, --window <windowid>   - specify a window to move relative to.
You specified the wrong number of args (expected 2 coordinates or 'restore').
david@davidorlow-pc:~$ xdotool mousemove --screen 0 1280 800
david@davidorlow-pc:~$ xdotool mousemove --screen 1 1280 1024
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  41 (X_WarpPointer)
  Resource id in failed request:  0x18
  Serial number of failed request:  19
  Current serial number in output stream:  21
david@davidorlow-pc:~$ 


```I think that's what the thread said to do.

---

### Post by dorlow on 2012-02-10
More I look at it, I don't think I have the numbers right in my command.  One monitor is 1280x800 and other is 1280x1024.  But I think I'm supposed to be putting in the positioning in the command, not the resolutions.

---

### Post by pqwoerituytrueiwoq on 2012-02-10
the use of xdotool in that thread was a neat way to use 2 screens independently

since both your screens have the same width (as far is resolution in concerned)
you an put one above the other and use twin view with no dead space

if you want the screens where they are now without dead space and no lag use metacity and disable xinerama you will not be able to drag windows between screens

---

### Post by dorlow on 2012-02-10
> **pqwoerituytrueiwoq said:**
> the use of xdotool in that thread was a neat way to use 2 screens independently

since both your screens have the same width (as far is resolution in concerned)
you an put one above the other and use twin view with no dead space

if you want the screens where they are now without dead space and no lag use metacity and disable xinerama you will not be able to drag windows between screens


Thing that makes me mad is somehow the first time I loaded Ubuntu 11.10, the screens just worked right... the way I want them to.  I can't remember what went wrong and why I had to redo the system.  I was just thinking they figured it out in 11.10.  If I knew that load would've been the last time it would ever work, I would've backed up my xorg.conf file and anything else I could find so I could've gotten it back.

So, seeing it did work once, I know it's possible.  Just no clue how to get it back.

---

### Post by dorlow on 2012-02-10
> **pqwoerituytrueiwoq said:**
> the use of xdotool in that thread was a neat way to use 2 screens independently

since both your screens have the same width (as far is resolution in concerned)
you an put one above the other and use twin view with no dead space

if you want the screens where they are now without dead space and no lag use metacity and disable xinerama you will not be able to drag windows between screens

I don't want to make my monitors believe they're on top of eachother.  That would be just as weird manoeuvring that way.  I'd like for it to just work right.  Although I was just reading Ubuntu 12.04 is supposed to have better dual monitor support... so maybe I just need to wait a few months for that to come out.

---

### Post by dorlow on 2012-02-10
One thing that I don't know if has anything to do with the problems I'm having is I absolutely hate the new Ubuntu interface, so I loaded the old gnome interface to feel more like 11.04.  Don't know if the old menus would mess with the dual monitor setup?

---

### Post by pqwoerituytrueiwoq on 2012-02-10
> Although I was just reading Ubuntu 12.04 is supposed to have better dual monitor support
really i hope so care to try the alpha/beta/daily?

there may be a backup of your old config settings
```
ls /etc/X11/
```

---

### Post by pqwoerituytrueiwoq on 2012-02-19
i found a solution for dual screens with no dead space and yuo can drag windows between screens :)
the open source nvidia driver nouveau does this perfectly on 11.10 with my asus Nvidia GTX 550 TI
good luck getting compiz though i did not even want to try that

---

