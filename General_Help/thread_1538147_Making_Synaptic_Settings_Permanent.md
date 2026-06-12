---
title: "Making Synaptic Settings Permanent"
date: 2010-07-24
forum: General Help
---

### Post by n1ghtley on 2010-07-24
I have been attempting to solve an issue with my Macbook 4.1's trackpad, and I have found the following commands to be effective:

synclient FingerLow=10
synclient FingerHigh=20

The only problem is that the changes do not persist after reboot.  Is there any way I can make the changes permanent?

Thanks in advance!!

---

### Post by n1ghtley on 2010-07-24
bump

---

### Post by dcstar on 2010-07-25
> **n1ghtley said:**
> I have been attempting to solve an issue with my Macbook 4.1's trackpad, and I have found the following commands to be effective:

synclient FingerLow=10
synclient FingerHigh=20

The only problem is that the changes do not persist after reboot.  Is there any way I can make the changes permanent?

Thanks in advance!!

[http://wiki.archlinux.org/index.php/Touchpad_Synaptics](http://wiki.archlinux.org/index.php/Touchpad_Synaptics)

---

### Post by v41 on 2010-07-25
I don't know a good way to do this, so I've posted an ugly-but-effective hack below.  

First a bit of history.  Once upon a time, these settings went into xorg.conf .  That was superseded by appletouch.fdi, but this no longer works in Lucid!  There is a file called /usr/lib/X11/xorg.conf.d/10-synaptics.conf, but I'm not sure how to alter it.

So now for the ugly hack.  

1) Click on Places -> Home Folder.  Right-click and select "Create Folder".  Name the new folder "bin" .  Move into the bin folder.  Right-click and select "Create Document -> Empty File".  Name the new file touchpad_settings_unique .  Create a second file called touchpad_settings_loop.sh  .

Here is the contents of the touchpad_settings_unique file:

```
#!/bin/bash
# (can't get sh to work)
# Try to prevent multiple copies of touchpad_settings_loop from running
if [ `ps gaxu | /bin/grep -v grep | /bin/grep -c touchpad_settings_loop` == 0 ] ; then
   $HOME/bin/touchpad_settings_loop.sh &
fi
exit
```Here is the contents of the touchpad_settings_loop.sh file:

```
#!/bin/sh
# touchpad settings:  
# (can't set these in appletouch.fdi, because either gnome or metacity or compiz  overrides them!)

while true; do

#
if [ `/usr/bin/synclient -l | /bin/grep -i fingerhigh | /bin/grep -c 20` -eq 0 ] ; then
   synclient FingerLow=10
   synclient FingerHigh=20
  #Some other possible settings.  Remove the # to activate the setting
  #synclient MinSpeed=0.4
  #synclient MaxSpeed=0.7
  #synclient AccelFactor=0.1
  #synclient Tapbutton2=2
  #synclient Tapbutton3=3
fi

sleep 10
done
```2) Right-click on each of the files you have created and select Properties.  Click on the Permissions tab and select "Allow executing file as program".

To test whether the script is working properly, open a terminal and then type the following:

```
cd bin
./touchpad_settings_unique &
```3) Click on "Sytem -> Preferences -> Startup Applications", then click on "Add".  In the "Name" box type "touchpad settings".  In the "Command" box click on "browse", and then select the file touchpad_settings_unique .

---

### Post by NoBugs! on 2010-07-26
> **v41 said:**
> 
First a bit of history.  Once upon a time, these settings went into xorg.conf .  That was superseded by appletouch.fdi, but this no longer works in Lucid!  There is a file called /usr/lib/X11/xorg.conf.d/10-synaptics.conf, but I'm not sure how to alter it.


run:
```
sudo gedit /usr/lib/X11/xorg.conf.d/10-synaptics.conf
```
then find the touchpad section and add these 3 lines to it:
```
Section "InputClass"
	Identifier "touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"

	Option "FingerLow" "10"
	Option "FingerHigh" "20"
	Option "SHMConfig" "on"
EndSection
```
Save and restart and it will work :)

---

### Post by v41 on 2010-07-26
> **NoBugs! said:**
> run:
```
sudo gedit /usr/lib/X11/xorg.conf.d/10-synaptics.conf
```then find the touchpad section and add these 3 lines to it:
```
Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"

    Option "FingerLow" "10"
    Option "FingerHigh" "20"
    Option "SHMConfig" "on"
EndSection
```Save and restart and it will work :)

Nice :p  I will give this a try.  Is the "SHMConfig" option still necessary?  Here's an extract from the synaptics man page:

> Option "SHMConfig" "boolean"
              Switch  on/off  shared  memory for run-time configuration. Note that this is considered a security risk since any user can access the configuration. This option is not needed with synaptics 1.0  or  later.  See  section  Device Properties.

DEVICE PROPERTIES
       Synaptics  1.0  and  higher support input device properties if the driver is running on X server 1.6 or higher. On these driver versions, Option "SHMConfig" is not needed to enable run-time configuration.  The  synclient  tool  shipped  with synaptics version 1.1 uses input device properties by default.  Properties supported:
Synclient works fine on Lucid without SHMConfig, so I expect/hope that the same will be true for 10-synaptics.conf .

---

### Post by v41 on 2010-07-27
> **NoBugs! said:**
> run:
```
sudo gedit /usr/lib/X11/xorg.conf.d/10-synaptics.conf
```then find the touchpad section and add these 3 lines to it:
```
Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"

    Option "FingerLow" "10"
    Option "FingerHigh" "20"
    Option "SHMConfig" "on"
EndSection
```Save and restart and it will work :)

OK, I tried this and it does indeed work :D   No need for SHMConfig.

I tried adding,

Option "TapButton2" "2"
Option "TapButton3" "3"

but this option gets overridden somewhere :(

---

### Post by v41 on 2010-07-28
> **v41 said:**
> 
I tried adding,

Option "TapButton2" "2"
Option "TapButton3" "3"

but this option gets overridden somewhere :(

This is a known [[COLOR=MediumTurquoise]_bug_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/563276") in the gnome-settings-daemon package.    It affects synaptics touchpads.  There is a ppa with a patched version of the package [[COLOR=MediumTurquoise]_here_[/COLOR]]("https://launchpad.net/%7Eyurivkhan/+archive/proposed/") .

---

### Post by strungoutfan78 on 2010-08-15
This has also worked for me, up until the login screen that is.  I used this to configure TapButton1 = 1 and was successful to a point.  Once I log in and KDE actually starts, the effects are overridden somehow.  Any ideas?

Also I'm actually using Fedora but I don't think there is much difference between the 2 in this particular situation.

---

### Post by blehmeco on 2011-02-15
> **v41 said:**
> I don't know a good way to do this, so I've posted an ugly-but-effective hack below.  

First a bit of history.  Once upon a time, these settings went into xorg.conf .  That was superseded by appletouch.fdi, but this no longer works in Lucid!  There is a file called /usr/lib/X11/xorg.conf.d/10-synaptics.conf, but I'm not sure how to alter it.

So now for the ugly hack.  

1) Click on Places -> Home Folder.  Right-click and select "Create Folder".  Name the new folder "bin" .  Move into the bin folder.  Right-click and select "Create Document -> Empty File".  Name the new file touchpad_settings_unique .  Create a second file called touchpad_settings_loop.sh  .

Here is the contents of the touchpad_settings_unique file:

```
#!/bin/bash
# (can't get sh to work)
# Try to prevent multiple copies of touchpad_settings_loop from running
if [ `ps gaxu | /bin/grep -v grep | /bin/grep -c touchpad_settings_loop` == 0 ] ; then
   $HOME/bin/touchpad_settings_loop.sh &
fi
exit
```Here is the contents of the touchpad_settings_loop.sh file:

```
#!/bin/sh
# touchpad settings:  
# (can't set these in appletouch.fdi, because either gnome or metacity or compiz  overrides them!)

while true; do

#
if [ `/usr/bin/synclient -l | /bin/grep -i fingerhigh | /bin/grep -c 20` -eq 0 ] ; then
   synclient FingerLow=10
   synclient FingerHigh=20
  #Some other possible settings.  Remove the # to activate the setting
  #synclient MinSpeed=0.4
  #synclient MaxSpeed=0.7
  #synclient AccelFactor=0.1
  #synclient Tapbutton2=2
  #synclient Tapbutton3=3
fi

sleep 10
done
```2) Right-click on each of the files you have created and select Properties.  Click on the Permissions tab and select "Allow executing file as program".

To test whether the script is working properly, open a terminal and then type the following:

```
cd bin
./touchpad_settings_unique &
```3) Click on "Sytem -> Preferences -> Startup Applications", then click on "Add".  In the "Name" box type "touchpad settings".  In the "Command" box click on "browse", and then select the file touchpad_settings_unique .

Thank you for this v41!
It surely ain't pretty, but who cares? It did the trick for me!
And I had been looking for this for quite a while now!

Cheers mate!


[I]EDIT:
[/I]
I've just remembered, that this could work for you guys too (it works for me) and it's not that complicated actually!

I just added these lines to a script I have in startup applications (hi: ntthe trick is in the *sleep* line, obviously):

 ```
sleep 5
synclient RTCornerButton=8 RBCornerButton=10 LTCornerButton=11 LBCornerButton=12 FastTaps=1
```Hope it helps someone else!


Cheers!

---

