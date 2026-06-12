---
title: "Disable touchpad while typing"
date: 2010-06-23
forum: General Help
---

### Post by altonbr on 2010-06-23
I've read through [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) but I can't seem to disable my touchpad while typing (it seems to be extremely sensitive to touch).

I can't disable touchpad, else it will disable all X.org input
```
$ sudo aptitude purge xserver-xorg-input-synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  gsynaptics xserver-xorg-input-all 
The following packages will be REMOVED:
  xserver-xorg-input-synaptics{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 17 not upgraded.
Need to get 0B of archives. After unpacking 365kB will be freed.
The following packages have unmet dependencies:
  xserver-xorg-input-all: Depends: xserver-xorg-input-synaptics but it is not installable
  gsynaptics: Depends: xserver-xorg-input-synaptics but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
gsynaptics
xserver-xorg-input-all

Score is 188

Accept this solution? [Y/n/q/?
```

There is no Touchpad tab under "System > Preferences > Mouse".

I've tried installing gsynaptics but it returns this error: "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

Enabling SHMConfig doesn't seem to work: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

What else can I do?

---

### Post by bobcollard on 2010-06-23
Install gpointing-device-settings which has replaced gsynaptics.

---

### Post by altonbr on 2010-06-24
> **bobcollard said:**
> Install gpointing-device-settings which has replaced gsynaptics.
That only detects my mouse, not my touchpad.

---

### Post by bobcollard on 2010-06-24
> **altonbr said:**
> That only detects my mouse, not my touchpad.
After installing it you have to run the applet.  I set mine up in startup applications to run every boot up or restart.  Then the screen will have the attached menu.  You can also run it in Terminal:
> sudo gpointing-device-settings

---

### Post by jesuisbenjamin on 2010-06-24
did you try ```
sudo apt-get install touchfreeze
```?

---

### Post by wykedengel on 2010-06-29
Touchfreeze didn't work for me on my Aspire 4810T. There is a new version out 0.2.5, that isn't in the repos, but I don't know how to install tar files.

---

### Post by nothingspecial on 2010-06-29
```
syndaemon -d -t -i 1
```

The number 1 at the end of the command is the amount of seconds you want to
disable the touchpad for.

If you add that command to System > Preferences > Startup Applications, you 
will not have to type it every time you log on.

See man syndaemon for more options

---

### Post by wykedengel on 2010-06-30
I am going to give that a try.

---

### Post by altonbr on 2010-07-01
> **bobcollard said:**
> After installing it you have to run the applet.  I set mine up in startup applications to run every boot up or restart.  Then the screen will have the attached menu.  You can also run it in Terminal:```
sudo gpointing-device-settings 			 		
```

I know, hense why I said:

> **altonbr said:**
> That only detects my mouse, not my touchpad.

It doesn't seem to detect it... see screenshot.

> **jesuisbenjamin said:**
> did you try ```
sudo apt-get install touchfreeze
```?

Doesn't work, even when I run 'touchfreeze' or 'sudo touchfreeze' in the terminal.

> **nothingspecial said:**
> ```
syndaemon -d -t -i 1
```The number 1 at the end of the command is the amount of seconds you want to
disable the touchpad for.

If you add that command to System > Preferences > Startup Applications, you 
will not have to type it every time you log on.

See man syndaemon for more options

I receive```
Unable to find a synaptics device.
```after running... but I have a touchpad...

---

### Post by wykedengel on 2010-07-01
Thank you so much, it looks like it worked. I am now typing and the touchpad is acting like it should.

> **nothingspecial said:**
> ```
syndaemon -d -t -i 1
```

The number 1 at the end of the command is the amount of seconds you want to
disable the touchpad for.

If you add that command to System > Preferences > Startup Applications, you 
will not have to type it every time you log on.

See man syndaemon for more options

---

### Post by ardunarda on 2010-07-10
same problem my touchpad is seen a wheel mouse

---

### Post by altonbr on 2010-09-13
I'd like to announce, that for my machine (ASUS K72JR), the touchpad now has a tab in System > Preferences > Mouse in Ubuntu 10.10 Maverick Meerkat.

I can now enable/disable two-finger scrolling and most importantly, disable touchpad clicking while typing (and touchpad click in general).

---

### Post by Rodney9 on 2010-11-12
> **bobcollard said:**
> Install gpointing-device-settings which has replaced gsynaptics.

Thank You , That fixed my problem in Xubuntu.

---

### Post by Ian Sinclair on 2010-11-19
Same problem, Acer Aspire with Ubuntu 10.04 (not Remix), mouse menu had no touchpad tab. After I set up WiFi, however, the touchpad appeared. Perhaps the tab is set up only for notepads using WiFi?

---

### Post by bobcollard on 2010-11-19
> **Ian Sinclair said:**
> Same problem, Acer Aspire with Ubuntu 10.04 (not Remix), mouse menu had no touchpad tab. After I set up WiFi, however, the touchpad appeared. Perhaps the tab is set up only for notepads using WiFi?
Could be wifi or Bluetooth, either way you have to uncheck the boxes in that to make gpointing-device-settings work.  Otherwise you could have a problem.

---

### Post by JohnElway on 2010-11-19
I had the same issue (Ubuntu was detecting the touchpad as a wheel mouse) and was able to disable the touchpad using this command:

```
xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" "Device Enabled" 8 0
```

This command enables it again:

```
xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" "Device Enabled" 8 1
```

To enter these commands more easily you can either set them up as bash aliases or keyboard shortcuts to turn the touchpad on and off on the fly.

---

### Post by franco_1_1_83 on 2011-12-21
I solved this issue by installing **mouseemu** and running:

[INDENT][FONT="Courier New"]sudo mouseemu -typing-block 1000ms[/FONT][/INDENT]

NOTE: This will prevent you touchpad (or mouse) to work during a period of 1 second after you type the last char.
Not sure if this will affect games like First Person Shooters.

Hope this helps.

---

### Post by chrinabuntu on 2012-01-07
I just cover it with my driver's license.  ;O)

---

### Post by wykedengel on 2012-02-26
> **chrinabuntu said:**
> I just cover it with my driver's license.  ;O)

:popcorn: That was an awesome answer!

---

